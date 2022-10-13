*************************************************************************
   ____  ____ 
  /   /\/   / 
 /___/  \  /   
 \   \   \/    � Copyright 2016-2022 Xilinx, Inc. All rights reserved.
  \   \        This file contains confidential and proprietary 
  /   /        information of Xilinx, Inc. and is protected under U.S. 
 /___/   /\    and international copyright and other intellectual 
 \   \  /  \   property laws. 
  \___\/\___\ 
 
*************************************************************************

Vendor: Xilinx 
Reference Design Version: 1.13
readme.txt Version: 1.13
Date Last Modified: 04/29/2022
Date Created: 06/02/2016
Associated Filename: xtp427-us-plus-schematic-review-checklist.xls

Supported Device(s): UltraScale+ FPGA and Zynq UltraScale+ Devices
Purpose: This ZIP file contains the schematic review checklist
Document Reference: XTP427
   
*************************************************************************

Disclaimer: 

      This disclaimer is not a license and does not grant any rights to 
      the materials distributed herewith. Except as otherwise provided in 
      a valid license issued to you by Xilinx, and to the maximum extent 
      permitted by applicable law: (1) THESE MATERIALS ARE MADE AVAILABLE 
      "AS IS" AND WITH ALL FAULTS, AND XILINX HEREBY DISCLAIMS ALL 
      WARRANTIES AND CONDITIONS, EXPRESS, IMPLIED, OR STATUTORY, 
      INCLUDING BUT NOT LIMITED TO WARRANTIES OF MERCHANTABILITY, 
      NON-INFRINGEMENT, OR FITNESS FOR ANY PARTICULAR PURPOSE; and 
      (2) Xilinx shall not be liable (whether in contract or tort, 
      including negligence, or under any other theory of liability) for 
      any loss or damage of any kind or nature related to, arising under 
      or in connection with these materials, including for any direct, or 
      any indirect, special, incidental, or consequential loss or damage 
      (including loss of data, profits, goodwill, or any type of loss or 
      damage suffered as a result of any action brought by a third party) 
      even if such damage or loss was reasonably foreseeable or Xilinx 
      had been advised of the possibility of the same.

Critical Applications:

      Xilinx products are not designed or intended to be fail-safe, or 
      for use in any application requiring fail-safe performance, such as 
      life-support or safety devices or systems, Class III medical 
      devices, nuclear facilities, applications related to the deployment 
      of airbags, or any other applications that could lead to death, 
      personal injury, or severe property or environmental damage 
      (individually and collectively, "Critical Applications"). Customer 
      assumes the sole risk and liability of any use of Xilinx products 
      in Critical Applications, subject only to applicable laws and 
      regulations governing limitations on product liability.

THIS COPYRIGHT NOTICE AND DISCLAIMER MUST BE RETAINED AS PART OF THIS 
FILE AT ALL TIMES.

*************************************************************************

This readme file contains the following sections:

1. Revision History
2. Operating Instructions

*************************************************************************
1. Revision History 
*************************************************************************
Date		Version	Revision

06/02/16	1.0	Initial Xilinx release.

08/21/16	1.1	Swapped bank numbering between ZU9EG-FFVC900 and ZU9EG-FFVB1156
			Changed recommendation for PUD_C pullup from VCCO_0 to VCCAUX
			Changed options for VCCO_0 voltage from "1.5 - 3.3" to "1.5 - 1.8"
			Removed comment from VCCO_0 referring to CFGBVS
			Updated decoupling capacitor values based on update from UG583
			Updated PS_MGTRREF recommendation
			Updated PS_MGTRAVCC additional information
			Updated PS_MGTRAVTT additional information
			Separated NAND_CE_1, NAND_RB_N and NAND_DQS_OUT from the NAND MIO interface pin selection into their own pin selections
			Updated CKE pin recommendations for PS LPDDR4 interfaces
			Limited allowable MIO pin choices for SPI SS0/SS1/SS2 and SDIO POW_RST/WP/CD depending on SPI and SDIO MIO pin selection
			Updated PS DDR4/DDR3 CKE pin connection recommendations
			Removed VCCO_0 reference from POR_OVERRIDE
			Removed "VCCO Bank 0" row for Zynq devices
			Added to PERSTN recommendation to specify that it applies to the PL
			Added note to PERSTN recommendation
			Changed "MIG" to "Memory Interface" and updated recommendation
			Updated additional information for VCCINT to specify that other voltage settings are optional
			Updated additional information for VCCBRAM to specify that other voltage settings are optional
			Changed HR to HD for VCCO of unused I/O banks recommendation
			Added reference to PS_INIT_B in the additional info for POR_OVERRIDE
			Updated bitstream length for ZU7EV
			Added reference to UG1075 for MGTAVTT, MGTAVCC, and MGTVCCAUX
			Changed HR to HD for VRP recommendations
			Changed references for PG156 to PG213 for PERSTN
			Removed HR Termination row
			Added 0.9V option for applicable PS power supplies
			Changed PS ADC to SYSMON ADC for VCC_PSADC recommendation
			Added requirement to PS Power-on Reset
			Added to PS Power Supply Ramp Time to see above for the PL supply ramp times
			Added VCCINT_VCU power supply

03/02/17	1.2	Changed reference from VCCAUX to VCCO_0 for PUDC_B in configuration modes besides PS Configuration Boot Mode
			Updated power supply recommendations with information on combining power rails
			Added Power Measurement item to Power section
			Added CG and EG devices for Zynq UltraScale+ MPSoC
			Updated VCCADC recommendations to replace ferrite bead with filter
			Changed PS DDR3 CKE termination from 39 ohms to 36 ohms
			Updated PS_POR_B and PS_REF_CLK to reference VCC_PSIO[3]
			Added a note to GC when a VCU device is chosen
			Added eMMC info info to SDIO for PSMIO Interfaces
			Added a pointer to "Configuring Multiple FPGAs" chapter of UG570 for DONE pin recommendations
			Updated PS_DDR_DM8, PS_DDR_DQS_N8, and PS_DDR_DQS_P8 connection recommendations
			Updated decoupling capacitor values based on update from UG583
			Added a user guide reference to PS_PADI/PS_PADO
			Update PS_ERROR_OUT and PS_ERROR_STATUS with LED recommendation
			Updated I2C_SCLK and I2C_SDA with changed figure name
			Updated SMBALERT with pullup resistor and pointer to user guide figure
			Updated PS_DDR_ALERT_N, PS_DDR_CK, and PS_DDR_CK_N to change VCC and VCCO to VCCO_PSDDR
			Swapped MOSI and MISO pins for SPI interfaces

09/07/17	1.3	Updated D[31:00] to reference D02 and D03 to VCCO_0 instead of VCCO_65 for SPI x4/x8
			Specified that MGT power supply decoupling applies "per power supply group"
			Changed VCC_PSIO decoupling from "per device" to "per rail"
			Added VU9P-FSGD2104, VU11P-FSGD2104 and VU13P-FIGD2104
			Added RSVDGND pin
			Added a link to UG1075 for PSDDR pin swapping restrictions
			Updated additional information for GC when selecting devices with a VCU core
			Updated PS DDR4 ALERT_N recommendations
			Added decoupling capacitors to VCCADC and VREFP
			Updated decoupling capacitor values for PS_MGTRAVCC and PS_MGTRAVTT
			Changed instances of PS_DONE_B to PS_DONE
			Updated VCCO_PSIO combined rails recommendations
			Removed VCC_PSPLL rail combination option from MGTVCCAUX
			Updated recommendations for SPI MIO interface pins
			Updated recommendations for PJTAG MIO interface pins
			Fixed issue with MIO pins for QSPI, PMU, and GPIO overwriting selected MIO pins for other interfaces
			Corrected HD banks for FFVE1156 packages
			Added bitstream length for VU11P, and VU13P devices
			Updated bitstream length for KU3P, KU5P and KU9P devices
			Changed VCC_PSINTFP from 0.85V to 0.9V for -3E devices

03/23/18	1.4	Changed VCCINT_VCU to 0.9V for all speed grades and updated rail combination guidelines accordingly
			Updated PS_INIT_B and PS_PROG_B to specify that the connection should be open-drain
			Removed delay requirement for GEM CCLK pins
			Removed 0.9V option for PS_MGTRAVCC in -3 speed grade
			Added a note on PS_DDR_DQ32-DQ63 stating that they should not be swapped with DQ0-DQ31 in 32-bit interfaces
			Added option to choose MIO26 for GEM_TSU
			Added pull-up recommendation for QSPI MIO interfaces
			Added a pointer to UG583 for the Memory Controller line item
			Updated PS_INIT_B recommendation to address issue with additional load
			Added info on 680 킚 capacitors to Additional Information for VCCINT
			Updated recommendation for unused ADC_VIN pins
			Updated recommendation for VCCSDFEC
			Added recommendations for unused ADC and DAC power pins
			Corrected HD banks for SFVC784 for ZU4 and ZU5 devices
			Fixed Device Migration to show all migratable devices
			Updated MGTAVTTRCAL and MGTRREF with recommendations for unused power supply groups
			For PS_SRST_B and PS_POR_B, changed VCCO_PSIO[3] to VCCO_MIO0
			Added note regarding LBIST for PS_PROG_B
			Increased package delay skew for QSPI MIO Interface
			Updated resistance value and package delay limits for SDIO_eMCC pins
			Increased package delay skew for TTC MIO Interface
			Increased package delay skew for SWDT MIO Interface
			Lowered trace delay and removed matching requirement for UART MIO Interface
			Lowered package delay and skew and added resistors for USB MIO Interface
			Lowered package skew for CAN MIO Interface
			Lowered package skew for NAND MIO Interface
			Added resistor precision for ADC_REXT and DAC_REXT
			Removed HBM_DA and HBM HPHY pins (replaced with RSVD and RSVDGND)
			Reordered list of PS MIO Interfaces
			Updated connection recommendations for PS DDR power pins when PS DDR is unused
			Changed instances of "full processor domain" to "full-power domain"

09/11/18	1.5	Updated PS_DDR_ODT connection for LPDDR4 to match UG583
			Added a pull-up resistor for Data 3 pin on PS SDIO interfaces on the SD side
			Specified that VCCO_PSDDR should not be combined with other power rails
			Corrected number of decoupling capacitors for ZU29DR-FFVF1760
			Added functionality to hide/show RSVDGND and VCCINT_VCU depending on whether they exist in the device chosen
			Changed VCCO_MIO0 to VCCO_PSIO[3] for PS_SRST_B and PS_POR_B
			Fixed issue with CAN0_CLK and CAN1_CLK MIO pin selection
			Added guidance for VCC_PSBATT when unused
			Added to Additional Information for MIO SDIO interfaces
			Added VU13P-FSGA2577
			Added UltraScale+ RFSoC lidless (FS) packages
			Added MTS and PL_SYSREF for RFSoC DAC/ADC
			Added -2LI speed grade
			Changed font size to fix issue with text being cut off while not at 100% zoom
			Added note for choosing ruggedized packages
			Added maximum voltage ripple for ADC/DAC power supplies
			Changed UG582 references to UG583
			Added to ADC_VIN recommendations
			Added to DAC_VOUT recommendations
			Added to MTS recommendations
			Updated VCM01/VCM23 recommendations
			Added to VCCSDFEC recommendations
			Updated speed grade options

12/13/18	1.6	Added VU27P and VU29P
			Updated decoupling guidelines for VU13P to account for shared/unshared VCCINT rail
			Added GTM section
			Added a note for VCCAUX_IO for XQ ruggedized packages
			Changed VCCO_PSIO[0 to VCCO_PSIO[3] for PS_SRST_B and PS_POR_B
			Fixed error with HP/HD bank numbers for ZU6 and ZU15 in FFVC900 and FFVB1156 packages
			Added details for DC coupled mode for SYSREF_N/P

07/03/19	1.7	Changed pull-up requirement for FWE_FCS2_B to 2.4kO for SPIx8 configuration mode
			Updated VCCAUX_IO note on XQ pacakges
			Updated guidelines for unused PS_MGTR pins
			Added "RFSoC" to title
			Removed x64 options for PSDDR interface selection for ZU2/ZU3 SBVA484/SFVA625
			Removed recommendations to ground VCCO pins for unused banks
			Removed option for using MIO26 for GEM_TSU
			Added link to UG578 for GTY documentation
			Changed MIO selection options for NAND_RB_N
			Corrected VCCAUX decoupling capacitors for ZU3CG/ZU3EG SBVA484/SFVA625
			Added ZU39DR
			Added DDR4 16-bit to PS_DDR options
			Removed 10 mV noise limit for VCCINT_GT and added clarification on power supply groups
			Added ability to format row/column height/width
			Removed option to share power rails with VCCINT_VCU for rails
			Added note for tying VCCINT_VCU to gnd when unused
			Added dFUSE note in PS Config section

11/27/19	1.8	Added VU19P device
			Updated decoupling guidelines per UG583 updates
			Reversed VCCAUX_HBM and VCC_IO_HBM lines
			Updated PERSTN pin recommendations to align with PG213

06/05/20	1.9	Removed pull-up recommendation for PS_JTAG_TDO
			Updated recommendation for PS_REF_CLK with regards to signal integrity
			Added note to PERSTN recommendation related to bank 65 usage
			Updated QSPI and QSPI_LPBK pin recommendations to match updates for UG583
			Removed �9 ps matching recommendation for GEM MIO interface pins
			Fixed recommendation for VCCO decoupling per bank vs. 4 banks
			Updated decoupling capacitor values for VCC_PSDDR_PLL based on UG583 updates
			Fixed issue with VU7P-FLVA2104 device power supply recommendations
			Updated VCC_PSINTFP and VCC_PSINTFP_DDR combining recommendations per DS925

11/13/20	1.10	Added KU19P, VU23P and VU57P devices
			Removed RSVDGND for devices where not applicable
			Updated VCCO_0 decoupling
			Removed pull-up recommendation for SPI MOSI/MISO pins

06/30/21	1.11	Added UBVA530 package for ZU2 and ZU3 devices
			Updated recommendations for VCCO_PSDDR rail sharing
			Fixed tile number error for DAC power rails and added that tile number limitation is specifically when using MTS
			Added note for inter-byte clocking to GC pin recommendations
			Fixed error for Bank 0 VCCO decoupling recommendations
			Added power up/down requirements for ADC_AVCC and ADC_AVCCAUX for certain RFSoC devices
			Updated power supply sequencing to alight better with datasheet requirements
			Added notes regarding clock forwarding for ADC/DAC clocking
			Updated recommendation for PS_DDR_BG1 pin for PS DDR4 64-bit 1Rank interfaces

12/15/21	1.12	Added Artix UltraScale+ devices
			Added Zynq UltraScale+ MPSoC and RFSoC devices (ZU1CG, ZU1EG, ZU42DR, ZU65DR, and ZU67DR)
			Added note to PS_MGTREFCLK regarding PS_POR_B
			Added note for AC coupling capacitors for RF DAC and ADC I/Os
			Revised recommendations for unused RF ADC I/Os
			Added recommendation for TDD power saving mode for RF ADC/DAC power supply pins
			Added notes on clock forwarding for DAC_CLK pins

04/29/22	1.13	Removed references to PS power rails for devices without PS
			Fixed error when selecting Artix UltraScale+ devices
			Updated reference to Full Power Management Flexibility for combined rail recommendations
			Added pull-up resistor recommendation for eMMC CMD


*************************************************************************
2. Operating Instructions 
*************************************************************************

!	Macros must be enabled for full functionality.
1.	This spreadsheet is intended to provide a list of what has been checked (and what has not been checked) during a customer schematic review. It is not intended to be a comprehensive checklist.
	
2.	The Project Info page gives an overview of the schematic that is being reviewed, and the person(s) performing the review. It also contains the Purpose and Disclaimer paragraphs.
	
3.	The Checklist pages contain some of the more common items that should be checked. In some cases, these items might not apply to a specific schematic review, and can be ignored. In other cases, there might be additional items that need to be checked. In that case, the user can add a line to the end of the worksheet.
	
4.	The Checklist pages are intended to collect information for a single FPGA/MPSoC and its supporting device (such as configuration memory). At the top of the Checklist page, the device part number and reference designator need to be recorded. If there are multiple devices, a workbook should be created for each device.
	
5.	"Each cell in the Status column has a pull-down menu with the color-coded selections OK, CHECK, and PROBLEM. The Status column allows the customer to quickly see the results of the schematic review.
� OK: The item receives reviewer approval.
� CHECK: The reviewer does not have sufficient information to determine if the item is OK or poses a PROBLEM. The designer must research the item and provide additional information.
� PROBLEM: There is an issue with the item. PROBLEM flags the item for the designer, who needs to research the issue and find a solution.
� Not Checked: The item has not been checked and might require additional attention.
� N/A: The item is not applicable to this device or design."
	
6.	The Actual Implementation column can be used to provide additional clarification. This information is especially important if the item is tagged with CHECK or PROBLEM.
