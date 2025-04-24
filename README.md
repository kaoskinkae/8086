# Naming devices not declared in our ACPI SSDT 8086

We can customize the values ​​not present in Ioreg named 8086 with names that are visible to devices not present on a Mac but present on our computer. The process is to create an SSDT named SSDT-8086 with all the devices present on our system but not recognized by a Mac. This is only a customization of the name present and visible in both Hackintool and Ioreg and does not affect the operation of our computer.

![Captura de pantalla 2025-04-24 a las 14 41 34](https://github.com/user-attachments/assets/6a5cf0a1-9698-4de1-a928-5d2a01e6cc09)


## EXAMPLE

![Captura de pantalla 2025-04-24 a las 14 54 14](https://github.com/user-attachments/assets/c4da1206-7479-45d8-a35a-0a61e9165bc3)


In the SSDT, we have the Device that we want to use, for example THTC, then we assign

**"AAPL,slot-name",**

$${\color{red}Red}$$	Internal@0,18,0",

**"model",**

"Intel Corporation, Series Chipset PCH Thermal Controller"

**"name",**

"Signal Processing Controller"

**"device_type",**

"Signal Processing Controller"

-------------------------------------------------------------------

pci8086,a379

Internal@0,31,0

PciRoot(0x0)/Pci(0x12,0x0)

THTC

![Captura de pantalla 2025-04-24 a las 15 09 43](https://github.com/user-attachments/assets/c8f5c3d0-bffc-47c1-b4a8-c971fe6e1890)

![Captura de pantalla 2025-04-24 a las 15 13 41](https://github.com/user-attachments/assets/284aea0d-e1f4-4089-9ad8-1263ae92a07f)




The values ​​can be extracted from PCIe Hackintool and also from OCC in Device Properties

SSDT-8086.aml we can create a complete with all the values ​​not present in our Mac

![Captura de pantalla 2025-04-24 a las 17 22 57](https://github.com/user-attachments/assets/ecd798c1-fdb0-4f6c-bf11-daa5233442df)


## Hackintool *pcidevices.dsl* Name (_ADR, 0x00120000)  // _ADR: Address

![Captura de pantalla 2025-04-24 a las 17 23 04](https://github.com/user-attachments/assets/d520b978-2a8f-4d1c-be57-e2e957b577ba)


 
## Activate the new name present in the SSDT “THTC”




