/**
 * Fare Calculator Utilities
 * 
 * ============================================================================
 * DATA SOURCE: BART Published Fare Information
 * ============================================================================
 * Fare structure based on BART's publicly available fare charts.
 * Source: bart.gov/tickets/fares
 * 
 * ⚠️ NOT REAL-TIME: Fares shown are based on published rates.
 * Actual fares may change. Always verify at bart.gov before travel.
 * ============================================================================
 */

import { STATIONS } from '../data/stations';
import { calculateDistance } from './geoUtils';

/**
 * BART Fare Configuration
 * Based on published BART fare structure (2024)
 * Source: bart.gov/tickets/fares
 */
export const FARE_CONFIG = {
  // Base fare structure
  baseFare: 2.15,      // Entry fee
  perMile: 0.295,      // Approximate per-mile rate
  maxFare: 15.95,      // Maximum one-way fare
  minFare: 2.15,       // Minimum fare
  
  // Airport surcharges (published rates)
  surcharges: {
    SFIA: 4.85,   // SFO Airport premium
    OAKL: 6.20,   // Oakland Airport (includes connector)
  },
  
  // Discount programs (official BART discount rates)
  // Source: bart.gov/tickets/discounts
  discounts: {
    adult: { 
      rate: 0, 
      label: "Adult", 
      icon: "👤", 
      desc: "Full fare",
      requirement: "Standard Clipper card"
    },
    youth: { 
      rate: 0.50, 
      label: "Youth (5-18)", 
      icon: "🧒", 
      desc: "50% discount",
      requirement: "Youth Clipper card required"
    },
    senior: { 
      rate: 0.625, 
      label: "Senior (65+)", 
      icon: "👴", 
      desc: "62.5% discount",
      requirement: "Senior Clipper card required"
    },
    disabled: { 
      rate: 0.625, 
      label: "Disabled (RTC)", 
      icon: "♿", 
      desc: "62.5% discount",
      requirement: "RTC Clipper card required"
    },
    clipperStart: { 
      rate: 0.50, 
      label: "Clipper START", 
      icon: "💳", 
      desc: "50% discount",
      requirement: "Income-qualified adults 19-64"
    },
    child: { 
      rate: 1.0, 
      label: "Child (4 & under)", 
      icon: "👶", 
      desc: "FREE",
      requirement: "No ticket needed, limit 2 per fare-paying adult"
    },
  }
};

/**
 * Real fare data between select station pairs
 * Source: BART fare charts (bart.gov/tickets/fares)
 * Used to calibrate distance-based calculations
 */
export const SAMPLE_FARES = {
  'EMBR-DALY': 5.10,
  'EMBR-RICH': 5.90,
  'EMBR-PITT': 7.30,
  'EMBR-DUBL': 6.90,
  'EMBR-MLBR': 5.90,
  'EMBR-SFIA': 10.75, // Includes airport surcharge
  '12TH-SFIA': 11.90, // Includes airport surcharge
  'DALY-RICH': 8.25,
  'BALB-OAKL': 10.75, // Includes airport surcharge
};

/**
 * Calculate fare between two stations
 * Uses distance-based calculation calibrated to published fares
 * 
 * @param {string} fromAbbr - Origin station abbreviation
 * @param {string} toAbbr - Destination station abbreviation
 * @param {string} passengerType - Type of passenger
 * @returns {object|null} - Fare information
 */
export const calculateFare = (fromAbbr, toAbbr, passengerType = 'adult') => {
  // Same station = no fare
  if (fromAbbr === toAbbr) {
    return { 
      fare: 0, 
      discountedFare: 0, 
      distance: 0, 
      savings: 0,
      source: 'N/A'
    };
  }
  
  const from = STATIONS[fromAbbr];
  const to = STATIONS[toAbbr];
  
  if (!from || !to) return null;
  
  // Calculate distance
  const distance = calculateDistance(from.lat, from.lng, to.lat, to.lng);
  
  // Check if we have an exact published fare
  const fareKey = `${fromAbbr}-${toAbbr}`;
  const reverseFareKey = `${toAbbr}-${fromAbbr}`;
  let baseFare;
  let source;
  
  if (SAMPLE_FARES[fareKey]) {
    baseFare = SAMPLE_FARES[fareKey];
    source = 'Published fare chart';
  } else if (SAMPLE_FARES[reverseFareKey]) {
    baseFare = SAMPLE_FARES[reverseFareKey];
    source = 'Published fare chart';
  } else {
    // Calculate based on distance
    baseFare = FARE_CONFIG.baseFare + (distance * FARE_CONFIG.perMile);
    
    // Add airport surcharges if applicable
    if (FARE_CONFIG.surcharges[fromAbbr]) {
      baseFare += FARE_CONFIG.surcharges[fromAbbr];
    }
    if (FARE_CONFIG.surcharges[toAbbr]) {
      baseFare += FARE_CONFIG.surcharges[toAbbr];
    }
    
    // Apply min/max limits
    baseFare = Math.max(FARE_CONFIG.minFare, Math.min(FARE_CONFIG.maxFare, baseFare));
    source = 'Calculated from distance';
  }
  
  // Round to nearest nickel (BART standard)
  baseFare = Math.round(baseFare * 20) / 20;
  
  // Apply discount
  const discount = FARE_CONFIG.discounts[passengerType]?.rate || 0;
  const discountedFare = discount === 1.0 ? 0 : baseFare * (1 - discount);
  
  // Round discounted fare
  const roundedDiscountedFare = Math.round(discountedFare * 20) / 20;
  
  return {
    fare: baseFare,
    discountedFare: roundedDiscountedFare,
    distance: Math.round(distance * 10) / 10,
    savings: Math.round((baseFare - roundedDiscountedFare) * 100) / 100,
    passengerType,
    source,
    disclaimer: 'Based on published fares. Verify at bart.gov before travel.'
  };
};

/**
 * Get discount info for a passenger type
 */
export const getDiscountInfo = (passengerType) => {
  return FARE_CONFIG.discounts[passengerType] || FARE_CONFIG.discounts.adult;
};

/**
 * Get all available discount types
 */
export const getAllDiscounts = () => {
  return Object.entries(FARE_CONFIG.discounts).map(([key, value]) => ({
    type: key,
    ...value
  }));
};

export default calculateFare;
