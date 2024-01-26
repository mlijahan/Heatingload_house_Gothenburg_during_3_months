# AUTOMATING BUILDING ENERGY PERFORMANCE SIMULATIONS

The base model that is simulated in this script is a residential building based in Gothenburg, Sweden. In this scriptis the heating load of the building during the first cold third months in 2019 using datasets of urban climate data (2019.csv) is simulated the heating load of the building during the first cold third months in 2019 using datasets of urban climate data (2019.csv). Formulations are based on ASHRAE 2021. 
Basemodel.pdf file shows readily the details of the building. Revit 20121 is used to simulate this model,  then using the schedule option the exported Excel files of the component’s properties are provided as follows:

1- envelopes_properties.csv : envelopes areas, U and R factors of Floors, Walls and Ceiling.
2- doors.csv : properties of doors as the fenestration
3- windows.csv : properties of windows as the fenestration


![newplot (2)](https://github.com/mlijahan/Heatingload_house_Gothenburg_during_3_months/assets/89294710/6cf34166-3d3f-4e18-af44-df724b7243af) <br>


![newplot (4)](https://github.com/mlijahan/Heatingload_house_Gothenburg_during_3_months/assets/89294710/24844b34-bfa9-4239-86db-08ece638de58) <br>

![newplot (5)](https://github.com/mlijahan/Heatingload_house_Gothenburg_during_3_months/assets/89294710/a6863761-a14d-40ac-9191-884e3833667a) <br>



Some of the output of this script showed here. With manipulation with temerature design and inside temperature, the output will changes. Simulation of other heating load building models using the other .CSV files and changing 3 factors inside the script (from ASHRAE) for new model is possible.
