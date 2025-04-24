# Renaming Devices Using SSDT 8086
We can customize the values ​​not present in Ioreg named 8086 with names that are visible to devices not present on a Mac but present on our computer. The process is to create an SSDT named SSDT-8086 with all the devices present on our system but not recognized by a Mac. This is only a customization of the name present and visible in both Hackintool and Ioreg and does not affect the operation of our computer.

![Captura de pantalla 2025-04-24 a las 14 41 34](https://github.com/user-attachments/assets/6a5cf0a1-9698-4de1-a928-5d2a01e6cc09)


EXAMPLE

![Captura de pantalla 2025-04-24 a las 14 54 14](https://github.com/user-attachments/assets/c4da1206-7479-45d8-a35a-0a61e9165bc3)


In the SSDT, we have the Device that we want to use, for example THTC, then we assign

"AAPL,slot-name",
"Internal@0,18,0",
"model",
"Intel Corporation, Series Chipset PCH Thermal Controller"
"name",
"Signal Processing Controller"
"device_type",
"Signal Processing Controller"

pci8086,a379
Internal@0,31,0
PciRoot(0x0)/Pci(0x12,0x0)
THTC

The values ​​can be extracted from PCIe Hackintool and also from OCC in Device Properties

SSDT-8086.aml we can create a complete with all the values ​​not present in our Mac

Name (_ADR, 0x00120000)  // _ADR: Address
Method (_DSM, 4, NotSerialized)  // _DSM: Device-Specific Method
        {
            If ((Arg2 == Zero))
            {
                Return (Buffer (One)
                {
                     0x03                                             // .
                })
            }

Hackintool pcidevices.dsl Name (_ADR, 0x00120000)  // _ADR: Address


Method (_STA, 0, NotSerialized)  // _STA: Status
        {
            If (_OSI ("Darwin"))
            {
                Return (0x0F)
            }
            Else
            {
                Return (Zero)
            }
        }
    }
 
Activate the new name present in the SSDT “THTC”




