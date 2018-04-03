# mortgage-js
Javascript Mortgage Calculator.

## Usage
    mortgageJs = require("./index")
    
    let mortgageCalculator = mortgageJs.createMortgageCalculator();
    mortgageCalculator.totalPrice = 800000;
    mortgageCalculator.downPayment = 160000;
    mortgageCalculator.interestRate = 0.045;
    mortgageCalculator.months = 360;
    mortgageCalculator.taxRate = 0.012;
    mortgageCalculator.insuranceRate = 0.0013;
    mortgageCalculator.mortgageInsuranceRate = 0.010;
    mortgageCalculator.mortgageInsuranceEnabled = true;
    mortgageCalculator.mortgageInsuranceThreshold = 0.2;
    mortgageCalculator.additionalPrincipalPayment = 100;
    let payment = mortgageCalculator.calculatePayment();

## Alternate Usage
    mortgageJs = require("./index")
    
    let payment = mortgageJs.calculatePayment(800000,
            160000,
            0.045,
            360,
            0.012,
            0.0013,
            0.010,
            true,
            0.2,
            100);

## Payment Model
    {
        loanAmount: number, // Total loan amount. Price - Down Payment
        principalAndInterest: number, // Portion of payment that goes towards principal & interest.
        tax: number, // Property tax
        insurance: number, // Homeowner insurance
        total: number, // Total monthly payment
        termMonths: number, // Number of monthly payments
        mortgageInsurance: number, // Private mortgage insurance. Only relevant with lower down payments.
        paymentSchedule: [
            {
                count: number, // The payment number starting with 1
                interestPayment: number, // The portion of payment that is an interest charge
                totalInterest: number, // The total interest that has been paid thus far
                principalPayment: number, // The portion of payment that goes towards the principal balance
                totalPayment: number, // The total payment amount
                totalPayments: number, // The total of payments that have been made thus far
                balance: number // The remaining balance after payment has been applied
            }
        ]
    }