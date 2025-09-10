---
uid: unitsOfMeasure
---

# Units of measure and quantities

The Sequential Data Store (SDS) provides a collection of built-in units of measure (UOM). These units of measure can be [associated](#associating-a-unit-of-measure-with-a-type) with streams and types to provide unit information for stream data that model measurable quantities. If data has unit information associated with it, SDS supports unit conversions when retrieving data. For more information, see [Reading data](xref:sdsReadingData).

Because a UOM (meter, for example) defines the magnitude of a quantity (for example, length), SDS represents this by way of two objects: SdsUom and SdsUomQuantity.

## SdsUom

SdsUom represents a single unit of measure, such as 'meter'.

The following table lists the required and optional SdsUom fields.

| Property | Type | Optionality | Details | Example |
| --- | --- | --- | --- | --- |
| Id | String | Required | Unique identifier for the unit of measure. | meters per second |
| Abbreviation | String | Optional | Abbreviation for the unit of measure. | m/s |
| Name | String | Optional | Full name for the unit of measure. | Meters per second |
| DisplayName | String | Optional | Friendly display name for the unit of measure. | meters per second |
| QuantityId | String | Required | The identifier associated with the quantity that this unit is a measure of. | Velocity |
| ConversionFactor | Double | Required | Used for unit conversions. When a value of this unit is multiplied by the ConversionFactor and then incremented by the ConversionOffset, the value in terms of the base unit of the corresponding quantity is returned. | 1.0 |
| ConversionOffset | Double | Required | Used for unit conversions. See details for ConversionFactor. | 0.0 |
| CreatedDate | DateTime | Set by server | Timestamp in ISO 8601 extended format and UTC time standard when the SdsUom was created. Cannot be modified by users. | 0001-01-01T00:00:00Z |
| ModifiedDate | DateTime | Set by server | Timestamp in ISO 8601 extended format and UTC time standard when the SdsUom was last modified. Cannot be modified by users. | 0001-01-01T00:00:00Z |

## SdsUomQuantity

SdsUomQuantity represents a single measurable quantity (for example, length).

The following table shows the required and optional SdsUomQuantity fields.

| Property | Type | Optionality | Details | Example |
| --- | --- | --- | --- | --- |
| Id | String | Required | Unique identifier for the quantity. | Velocity |
| Name | String | Optional | Full name for the quantity. | Velocity |
| BaseUom | SdsUom | Required | The base unit of measure for this quantity. All other Uom's measuring this quantity will have ConversionFactor's and ConversionOffsets relative to the BaseUom. | SdsUom representing "meters per second" |
| Dimensions | short[] | Optional | Reserved for internal use. Represents the seven base SI dimensions: Length, Mass, Time, Electric Current, Thermodynamic Temperature, Amount of Substance, and Luminous Density. | [1,0,-1,0,0,0,0] |
| CreatedDate | DateTime | Set by server | Timestamp in ISO 8601 extended format and UTC time standard when the SdsUomQuantity was created. Cannot be modified by users. | 0001-01-01T00:00:00Z |
| ModifiedDate | DateTime | Set by server | Timestamp in ISO 8601 extended format and UTC time standard when the SdsUomQuantity was last modified. Cannot be modified by users. | 0001-01-01T00:00:00Z |

## Supported system-defined unit quantities

Supported quantities and their base units of measure are listed below. Supported quantities are read-only.

| Quantity Id                                 | Base Uom Id               |
| ------------------------------------------- | ------------------------- |
| Acceleration                                | meter per square second   |
| Angular Velocity                            | radian per second         |
| Area                                        | square meter              |
| Computer Storage                            | byte                      |
| Conductivity                                | siemens per meter         |
| Density                                     | kilogram per cubic meter  |
| Dynamic Viscosity                           | pascal second             |
| Electric Charge                             | coulomb                   |
| Electric Current                            | ampere                    |
| Electric Potential                          | volt                      |
| Electric Resistance                         | ohm                       |
| Energy                                      | joule                     |
| Energy per Length                           | joule per meter           |
| Entropy and Heat Capacity                   | joule per kelvin          |
| Force                                       | newton                    |
| Frequency                                   | hertz                     |
| Illuminance                                 | lux                       |
| Irradiance                                  | watt per square meter     |
| Length                                      | meter                     |
| Luminous Intensity                          | candela                   |
| Mass                                        | kilogram                  |
| Mass Flow Rate                              | kilogram per second       |
| Molar Flow Rate                             | mole per second           |
| Molecular Weight                            | kilogram per mole         |
| Amount of Substance                         | mole                      |
| Plane Angle                                 | radian                    |
| Power                                       | watt                      |
| Pressure                                    | pascal                    |
| Quantity                                    | count                     |
| Quantity per Volume                         | count per cubic meter     |
| Ratio                                       | percent                   |
| Reciprocal length                           | inverse meter             |
| Specific Energy                             | joule per kilogram        |
| Specific Entropy and Specific Heat Capacity | joule per kilogram kelvin |
| Specific Volume                             | cubic meter per kilogram  |
| Speed                                       | meter per second          |
| Temperature                                 | kelvin                    |
| Temperature (Delta)                         | delta kelvin              |
| Time                                        | second                    |
| Volume                                      | cubic meter               |
| Volume Flow Rate                            | cubic meter per second    |

## Supported system-defined units of measure

Supported units of measure are listed below. Supported units of measure are read-only.

| Uom ID | Uom Name | Uom Abbrev | Quantity ID | Conversion Factor | Conversion Offset |
|--|--|--|--|--|--|
| count | count | count | Quantity | 1 | 0 |
| Ampere hour | Ampere hour | Ah | Electric Charge | 3600 | 0 |
| coulomb | coulomb | C | Electric Charge | 1 | 0 |
| kilogram per second | kilogram per second | kg/s | Mass Flow Rate | 1 | 0 |
| long ton per day | long ton per day | lton/d | Mass Flow Rate | 0.011759802 | 0 |
| million pound per day | million pound per day | MMlb/d | Mass Flow Rate | 5.24991169 | 0 |
| short ton per day | short ton per day | ston/d | Mass Flow Rate | 0.010499823 | 0 |
| thousand pound per day | thousand pound per day | klb/d | Mass Flow Rate | 0.005249912 | 0 |
| gram per second | gram per second | g/s | Mass Flow Rate | 0.001 | 0 |
| pound per second | pound per second | lb/s | Mass Flow Rate | 0.45359237 | 0 |
| tonne per day | tonne per day | t/d | Mass Flow Rate | 0.0115740740740741 | 0 |
| long ton | long ton | lton | Mass | 1016.046909 | 0 |
| million pound | million pound | MM lb | Mass | 453592.37 | 0 |
| ounce | ounce | oz | Mass | 0.028349523 | 0 |
| short ton | short ton | ston | Mass | 907.18474 | 0 |
| thousand pound | thousand pound | klb | Mass | 453.59237 | 0 |
| ton | ton | ton | Mass | 907.18474 | 0 |
| gram | gram | g | Mass | 0.001 | 0 |
| milligram | milligram | mg | Mass | 1.00E-06 | 0 |
| pound | pound | lb | Mass | 0.45359237 | 0 |
| tonne | tonne | t | Mass | 1000 | 0 |
| kilogram | kilogram | kg | Mass | 1 | 0 |
| second | second | s | Time | 1 | 0 |
| hour | hour | h | Time | 3600 | 0 |
| day | day | d | Time | 86400 | 0 |
| month | month | month | Time | 2628000 | 0 |
| week | week | week | Time | 604800 | 0 |
| year | year | yr | Time | 31536000 | 0 |
| minute | minute | min | Time | 60 | 0 |
| dyne | dyne | dyne | Force | 1.00E-05 | 0 |
| kilogram-force | kilogram-force | kgf | Force | 9.80665 | 0 |
| pound-force | pound-force | lbf | Force | 4.44822161526 | 0 |
| newton | newton | N | Force | 1 | 0 |
| watt | watt | W | Power | 1 | 0 |
| million British thermal unit per day | million British thermal unit per day | MM Btu/d | Power | 12211.29459 | 0 |
| million British thermal unit per hour | million British thermal unit per hour | MM Btu/h | Power | 293071.0702 | 0 |
| gigawatt | gigawatt | GW | Power | 1000000000 | 0 |
| megawatt | megawatt | MW | Power | 1000000 | 0 |
| British thermal unit per hour | British thermal unit per hour | Btu/h | Power | 0.29307107017222 | 0 |
| calorie per second | calorie per second | cal/s | Power | 4.1868 | 0 |
| horsepower | horsepower | hp | Power | 745.699871582 | 0 |
| joule per second | joule per second | J/s | Power | 1 | 0 |
| kilowatt | kilowatt | kW | Power | 1000 | 0 |
| megajoule per hour | megajoule per hour | MJ/h | Power | 277.777777777778 | 0 |
| million calorie per hour | million calorie per hour | MMcal/h | Power | 1163 | 0 |
| mole per second | mole per second | mol/s | Molar Flow Rate | 1 | 0 |
| gram mole per second | gram mole per second | gmol/s | Molar Flow Rate | 1 | 0 |
| kilogram mole per second | kilogram mole per second | kmol/s | Molar Flow Rate | 1000 | 0 |
| pound mole per second | pound mole per second | lbmol/s | Molar Flow Rate | 453.59237 | 0 |
| meter | meter | m | Length | 1 | 0 |
| centimeter | centimeter | cm | Length | 0.01 | 0 |
| inch | inch | in | Length | 0.0254 | 0 |
| International nautical mile | International nautical mile | nmi | Length | 1852 | 0 |
| kilometer | kilometer | km | Length | 1000 | 0 |
| millimeter | millimeter | mm | Length | 0.001 | 0 |
| foot | foot | ft | Length | 0.3048 | 0 |
| mile | mile | mi | Length | 1609.344 | 0 |
| sixteenth of an inch | sixteenth of an inch | sxi | Length | 0.0015875 | 0 |
| yard | yard | yd | Length | 0.9144 | 0 |
| micrometer | micrometer | μm | Length | 0.000001 | 0 |
| nanometer | nanometer | nm | Length | 0.000000001 | 0 |
| candela | candela | cd | Luminous Intensity | 1 | 0 |
| meter per second | meter per second | m/s | Speed | 1 | 0 |
| centimeter per second | centimeter per second | cm/s | Speed | 0.01 | 0 |
| foot per second | foot per second | ft/s | Speed | 0.3048 | 0 |
| International nautical mile per hour | International nautical mile per hour | nmi/h | Speed | 0.514444444444444 | 0 |
| kilometer per hour | kilometer per hour | km/h | Speed | 0.277777777777778 | 0 |
| mile per hour | mile per hour | mi/h | Speed | 0.44704 | 0 |
| revolution per minute | revolution per minute | rpm | Angular Velocity | 0.10471975511966 | 0 |
| radian per second | radian per second | rad/s | Angular Velocity | 1 | 0 |
| barrel per day | barrel per day | bbl/d | Volume Flow Rate | 1.84013072833333E-06 | 0 |
| cubic centimeter per second | cubic centimeter per second | cm3/s | Volume Flow Rate | 1.00E-06 | 0 |
| cubic foot per second | cubic foot per second | ft3/s | Volume Flow Rate | 0.028316846592 | 0 |
| cubic meter per hour | cubic meter per hour | m3/h | Volume Flow Rate | 0.000277777777777778 | 0 |
| Imperial gallon per minute | Imperial gallon per minute | Imp gal/min | Volume Flow Rate | 7.57681666666663E-05 | 0 |
| liter per second | liter per second | L/s | Volume Flow Rate | 0.001 | 0 |
| US gallon per minute | US gallon per minute | US gal/min | Volume Flow Rate | 6.30901964E-05 | 0 |
| cubic meter per second | cubic meter per second | m3/s | Volume Flow Rate | 1 | 0 |
| cubic foot per minute | cubic foot per minute | ft3/min | Volume Flow Rate | 0.000471947443 | 0 |
| pascal | pascal | Pa | Pressure | 1 | 0 |
| atmosphere | atmosphere | atm | Pressure | 101325 | 0 |
| bar | bar | bar | Pressure | 100000 | 0 |
| inches of mercury | inches of mercury | inHg | Pressure | 3386.38815789 | 0 |
| kilogram-force per square centimeter | kilogram-force per square centimeter | kgf/cm2 | Pressure | 98066.5 | 0 |
| kilogram-force per square meter | kilogram-force per square meter | kgf/m2 | Pressure | 9.80665 | 0 |
| kilopascal | kilopascal | kPa | Pressure | 1000 | 0 |
| millimeter of mercury | millimeter of mercury | mmHg | Pressure | 133.322368421 | 0 |
| newton per square meter | newton per square meter | N/m2 | Pressure | 1 | 0 |
| pound-force per square inch | pound-force per square inch | psi | Pressure | 6894.75729316836 | 0 |
| pound-force per square inch (customary) | pound-force per square inch (customary) | psia | Pressure | 6894.75729316836 | 0 |
| torr | torr | torr | Pressure | 133.322368421 | 0 |
| hectopascal | hectopascal | hPa | Pressure | 100 | 0 |
| millibar | millibar | mbar | Pressure | 100 | 0 |
| square meter | square meter | m2 | Area | 1 | 0 |
| square foot | square foot | ft2 | Area | 0.09290304 | 0 |
| acre | acre | acre | Area | 4046.856422 | 0 |
| square mile | square mile | mi2 | Area | 2589988.11 | 0 |
| square yard | square yard | yd2 | Area | 0.83612736 | 0 |
| hectare | hectare | ha | Area | 10000 | 0 |
| square centimeter | square centimeter | cm2 | Area | 0.0001 | 0 |
| square inch | square inch | in2 | Area | 0.00064516 | 0 |
| square kilometer | square kilometer | km2 | Area | 1000000 | 0 |
| square millimeter | square millimeter | mm2 | Area | 1.00E-06 | 0 |
| yobibyte | yobibyte | YiB | Computer Storage | 1.21E+24 | 0 |
| zebibyte | zebibyte | ZiB | Computer Storage | 1.18E+21 | 0 |
| exbibyte | exbibyte | EiB | Computer Storage | 1.15E+18 | 0 |
| pebibyte | pebibyte | PiB | Computer Storage | 1.13E+15 | 0 |
| tebibyte | tebibyte | TiB | Computer Storage | 1.10E+12 | 0 |
| gibibyte | gibibyte | GiB | Computer Storage | 1073741824 | 0 |
| mebibyte | mebibyte | MiB | Computer Storage | 1048576 | 0 |
| kibibyte | kibibyte | KiB | Computer Storage | 1024 | 0 |
| yottabyte | yottabyte | YB | Computer Storage | 1.00E+24 | 0 |
| zettabyte | zettabyte | ZB | Computer Storage | 1.00E+21 | 0 |
| exabyte | exabyte | EB | Computer Storage | 1.00E+18 | 0 |
| petabyte | petabyte | PB | Computer Storage | 1.00E+15 | 0 |
| terabyte | terabyte | TB | Computer Storage | 1.00E+12 | 0 |
| gigabyte | gigabyte | GB | Computer Storage | 1000000000 | 0 |
| megabyte | megabyte | MB | Computer Storage | 1000000 | 0 |
| kilobyte | kilobyte | kB | Computer Storage | 1000 | 0 |
| byte | byte | B | Computer Storage | 1 | 0 |
| kelvin | kelvin | K | Temperature | 1 | 0 |
| degree Celsius | degree Celsius | °C | Temperature | 1 | 273.15 |
| degree Rankine | degree Rankine | °R | Temperature | 0.555555556 | -2.56E-13 |
| degree Fahrenheit | degree Fahrenheit | °F | Temperature | 0.555555555555556 | 255.3722222 |
| milliampere | milliampere | mA | Electric Current | 0.001 | 0 |
| ampere | ampere | A | Electric Current | 1 | 0 |
| joule per gram | joule per gram | J/g | Specific Energy | 1000 | 0 |
| joule per kilogram | joule per kilogram | J/kg | Specific Energy | 1 | 0 |
| British thermal unit per pound | British thermal unit per pound | Btu/lb | Specific Energy | 2326 | 0 |
| kilocalorie per kilogram | kilocalorie per kilogram | kcal/kg | Specific Energy | 4186.8 | 0 |
| kilojoule per kilogram | kilojoule per kilogram | kJ/kg | Specific Energy | 1000 | 0 |
| kilojoule per pound | kilojoule per pound | kJ/lb | Specific Energy | 2204.62262184878 | 0 |
| British thermal unit per degree Rankine | British thermal unit per degree Rankine | Btu/°R | Entropy and Heat Capacity | 1899.100534716 | 0 |
| British thermal unit per degree Fahrenheit | British thermal unit per degree Fahrenheit | Btu/°F | Entropy and Heat Capacity | 1899.100534716 | 0 |
| kilojoule per kelvin | kilojoule per kelvin | kJ/K | Entropy and Heat Capacity | 1000 | 0 |
| joule per kelvin | joule per kelvin | J/K | Entropy and Heat Capacity | 1 | 0 |
| cubic foot per pound | cubic foot per pound | ft3/lb | Specific Volume | 0.0624279605761446 | 0 |
| cubic centimeter per gram | cubic centimeter per gram | cm3/g | Specific Volume | 0.001 | 0 |
| cubic meter per kilogram | cubic meter per kilogram | m3/kg | Specific Volume | 1 | 0 |
| hertz | hertz | Hz | Frequency | 1 | 0 |
| mole | mole | mol | Amount of Substance | 1 | 0 |
| gram mole | gram mole | gmol | Amount of Substance | 1 | 0 |
| kilogram mole | kilogram mole | kmol | Amount of Substance | 1000 | 0 |
| pound mole | pound mole | lbmol | Amount of Substance | 453.59237 | 0 |
| percent | percent | % | Ratio | 1 | 0 |
| decimal | decimal | decimal | Ratio | 100 | 0 |
| parts per billion | parts per billion | ppb | Ratio | 1.00E-07 | 0 |
| parts per million | parts per million | ppm | Ratio | 0.0001 | 0 |
| ohm | ohm | Ω | Electric Resistance | 1 | 0 |
| gram per gram mole | gram per gram mole | g/gmol | Molecular Weight | 0.001 | 0 |
| pound per pound mole | pound per pound mole | lb/lbmol | Molecular Weight | 0.001 | 0 |
| kilogram per mole | kilogram per mole | kg/mol | Molecular Weight | 1 | 0 |
| kilogram per kilogram mole | kilogram per kilogram mole | kg/kmol | Molecular Weight | 0.001 | 0 |
| British thermal unit per pound degree Rankine | British thermal unit per pound degree Rankine | Btu/(lb °R) | Specific Entropy and Specific Heat Capacity | 4186.8 | 0 |
| British thermal unit per pound degree Fahrenheit | British thermal unit per pound degree Fahrenheit | Btu/(lb °F) | Specific Entropy and Specific Heat Capacity | 4186.8 | 0 |
| joule per gram kelvin | joule per gram kelvin | J/(g K) | Specific Entropy and Specific Heat Capacity | 1000 | 0 |
| kilojoule per kilogram kelvin | kilojoule per kilogram kelvin | kJ/(kg K) | Specific Entropy and Specific Heat Capacity | 1000 | 0 |
| joule per kilogram kelvin | joule per kilogram kelvin | J/(kg K) | Specific Entropy and Specific Heat Capacity | 1 | 0 |
| kilovolt | kilovolt | kV | Electric Potential | 1000 | 0 |
| millivolt | millivolt | mV | Electric Potential | 0.001 | 0 |
| megavolt | megavolt | MV | Electric Potential | 1000000 | 0 |
| volt | volt | V | Electric Potential | 1 | 0 |
| joule | joule | J | Energy | 1 | 0 |
| gigawatt hour | gigawatt hour | GWh | Energy | 3.60E+12 | 0 |
| megawatt hour | megawatt hour | MWh | Energy | 3600000000 | 0 |
| watt hour | watt hour | Wh | Energy | 3600 | 0 |
| milliwatt hour | milliwatt hour | mWh | Energy | 3.60 | 0 |
| British thermal unit | British thermal unit | Btu | Energy | 1055.05585262 | 0 |
| calorie | calorie | cal | Energy | 4.1868 | 0 |
| gigajoule | gigajoule | GJ | Energy | 1000000000 | 0 |
| kilojoule | kilojoule | kJ | Energy | 1000 | 0 |
| kilowatt hour | kilowatt hour | kWh | Energy | 3600000 | 0 |
| megajoule | megajoule | MJ | Energy | 1000000 | 0 |
| watt second | watt second | Ws | Energy | 1 | 0 |
| kilocalorie | kilocalorie | kcal | Energy | 4186.8 | 0 |
| million calorie | million calorie | MMcal | Energy | 4186800 | 0 |
| million British thermal unit | million British thermal unit | MM Btu | Energy | 1055055853 | 0 |
| newton meter | newton meter | Nm | Energy | 1 | 0 |
| acre foot | acre foot | acre ft | Volume | 1233.481838 | 0 |
| million imperial gallon | million imperial gallon | Imp Mgal | Volume | 4546.09 | 0 |
| thousand imperial gallon | thousand imperial gallon | Imp kgal | Volume | 4.54609 | 0 |
| barrel | barrel | bbl | Volume | 0.158987295 | 0 |
| Imperial gallon | Imperial gallon | Imp gal | Volume | 0.00454609 | 0 |
| million US gallon | million US gallon | US Mgal | Volume | 3785.411784 | 0 |
| thousand US gallon | thousand US gallon | US kgal | Volume | 3.785411784 | 0 |
| cubic centimeter | cubic centimeter | cm3 | Volume | 1.00E-06 | 0 |
| cubic foot | cubic foot | ft3 | Volume | 0.028316846592 | 0 |
| kiloliter | kiloliter | kL | Volume | 1 | 0 |
| liter | liter | L | Volume | 0.001 | 0 |
| megaliter | megaliter | M L | Volume | 1000 | 0 |
| milliliter | milliliter | mL | Volume | 1.00E-06 | 0 |
| thousand cubic meter | thousand cubic meter | k m3 | Volume | 1000 | 0 |
| US gallon | US gallon | US gal | Volume | 0.003785411784 | 0 |
| million barrel | million barrel | MMbbl | Volume | 158987.2949 | 0 |
| thousand barrel | thousand barrel | kbbl | Volume | 158.9872949 | 0 |
| cubic meter | cubic meter | m3 | Volume | 1 | 0 |
| kilogram per cubic meter | kilogram per cubic meter | kg/m3 | Density | 1 | 0 |
| gram per liter | gram per liter | g/L | Density | 1 | 0 |
| kilogram per liter | kilogram per liter | kg/L | Density | 1000 | 0 |
| pound per barrel | pound per barrel | lb/bbl | Density | 2.85301017421182 | 0 |
| pound per cubic foot | pound per cubic foot | lb/ft3 | Density | 16.0184633739601 | 0 |
| pound per US gallon | pound per US gallon | lb/US gal | Density | 119.826427316897 | 0 |
| tonne per cubic meter | tonne per cubic meter | t/m3 | Density | 1000 | 0 |
| microgram per cubic meter | microgram per cubic meter | µg/m3 | Density | 1.0E-9 | 0 |
| radian | radian | rad | Plane Angle | 1 | 0 |
| degree | degree | ° | Plane Angle | 0.0174532925199433 | 0 |
| revolution | revolution | r | Plane Angle | 6.28318530717959 | 0 |
| pascal second | pascal second | Pa*s | Dynamic Viscosity | 1 | 0 |
| poise | poise | P | Dynamic Viscosity | 0.1 | 0 |
| delta degree Fahrenheit | delta degree Fahrenheit | delta °F | Temperature (Delta) | 0.555555555555556 | 0 |
| delta degree Rankine | delta degree Rankine | delta °R | Temperature (Delta) | 0.555555555555556 | 0 |
| delta kelvin | delta kelvin | delta K | Temperature (Delta) | 1 | 0 |
| delta degree Celsius | delta degree Celsius | delta °C | Temperature (Delta) | 1 | 0 |
| millimeter per square second | millimeter per square second | mm/s2 | Acceleration | 0.001 | 0 |
| meter per square second | meter per square second | m/s2 | Acceleration | 1 | 0 |
| decisiemens per meter | decisiemens per meter | dS/m | Conductivity | 0.1 | 0 |
| siemens per meter | siemens per meter | S/m | Conductivity | 1 | 0 |
| microsiemens per centimeter | microsiemens per centimeter | µS/cm | Conductivity | 0.0001 | 0 |
| count per liter | count per liter | Count/L | Quantity per Volume | 0.001 | 0 |
| count per cubic meter | count per cubic meter | Count/m3 | Quantity per Volume | 1 | 0 |
| watt-hours per mile | watt-hours per mile | Wh/mi | Energy per Length | 0.44704 | 0 |
| joule per meter | joule per meter | J/m | Energy per Length | 1 | 0 |
| inverse centimeter | inverse centimeter | cm-1 | Reciprocal Length | 100 | 0 |
| inverse meter | inverse meter | m-1 | Reciprocal Length | 1 | 0 |
| lux | lux | Lx | Illuminance | 1 | 0 |
| watt per square meter | watt per square meter | W/m2 | Irradiance | 1 | 0 |
| cubic meter per day | cubic meter per day | m3/d | Volume Flow Rate | 1.15740740740741E-05 | 0 |
| thousand barrels per day | thousand barrels per day | kbbl/d | Volume Flow Rate | 0.0018401307289352 | 0 |
| meter per minute | meter per minute | m/min | Speed | 0.0166666666666667 | 0 |
| pound per day | pound per day | lb/d | Mass Flow Rate | 5.249912E-06 | 0 |
| Imperial gallon per day | Imperial gallon per day | Imp gal/d | Volume Flow Rate | 5.261678240740741E-08 | 0 |
| US gallon per day | US gallon per day | US gal/d | Volume Flow Rate | 4.381263638888889E-08 | 0 |
| liter per day | liter per day | l/d | Volume Flow Rate | 1.15740740740741E-08 | 0 |
| liter per minute | liter per minute | l/min | Volume Flow Rate | 1.66666666666667E-05 | 0 |
| liter per hour | liter per hour | l/h | Volume Flow Rate | 2.77777777777778E-07 | 0 |
| thousand US gallon per hour | thousand US gallon per hour | US kgal/h | Volume Flow Rate | 0.00105150327333333 | 0 |
| thousand US gallon per minute | thousand US gallon per minute | US kgal/min | Volume Flow Rate | 0.0630901964 | 0 |
| thousand Imperial gallon per hour | thousand Imperial gallon per hour | Imp kgal/h | Volume Flow Rate | 0.00126280277777778 | 0 |
| thousand Imperial gallon per minute | thousand Imperial gallon per minute | Imp kgal/min | Volume Flow Rate | 0.0757681666666667 | 0 |
| cubic foot per hour | cubic foot per hour | ft3/h | Volume Flow Rate | 7.86579072000000E-06 | 0 |
| bushel | bushel | bu | Volume | 0.03523907016688 | 0 |
| kilogram per hour | kilogram per hour | kg/h | Mass Flow Rate | 0.000277777777777778 | 0 |
| kilojoule per hour | kilojoule per hour | kJ/h | Power | 0.277777777777778 | 0 |
| gram per cubic meter | gram per cubic meter | g/m3 | Density | 0.001 | 0 |
| millimeter per second | millimeter per second | mm/s | Speed | 0.001 | 0 |


## Associating a unit of measure with a type

At type creation, you can associate SdsUom with a [SdsTypeProperty](xref:sds-sdstypes-props#sdstypeproperty).

## Associating a unit of measure with a stream

At stream creation, you can override any unit of measure associated with an SdsTypeProperty belonging to the type of the stream. This override enables the reuse of a type that may have default unit information associated with it already. For more information, see [SdsStreamPropertyOverride](xref:sds-stream-properties#sdsstreampropertyoverride).
