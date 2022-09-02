# qb_ems_mechanic_duty

Ems & Mechanic go on and off duty Using QB-Target

qb-target/init.lua config.peds

{ --EMS Duty
  model = 's_m_m_doctor_01',
  coords = vector4(311.29, -599.22, 42.29, 51.56),
  freeze = true,
  invincible = true,
  blockevents = true,
  },
{ --LSC Duty
  model = 'mp_m_waremech_01',
  coords = vector4(-344.91, -123.15, 38.01, 222.85),
  freeze = true,
  invincible = true,
  blockevents = true,
  },

qb-target/init.lua config.targetmodels

    ["EMS On/Off Duty"] = {
        models = {
            "s_m_m_doctor_01"
        },
        options = {
            {
                type = "client",
                event = "Ambulance-Sign",
                icon = "fas fa-truck-medical",
                label = "Go On/Off Duty",
            }
        },
        distance = 3.5,
    },
    ["Mechanic On/Off Duty"] = {
        models = {
            "mp_m_waremech_01"
        },
        options = {
            {
                type = "client",
                event = "LSC-Sign",
                icon = "fas fa-wrench",
                label = "Go On/Off Duty",
            }
        },
        distance = 3.5,
    },

qb-ambulancejob/client/main.lua

RegisterNetEvent("Ambulance-Sign")
AddEventHandler("Ambulance-Sign", function()
    TriggerServerEvent("QBCore:ToggleDuty")
end)

qb-mechanicjob/client/main.lua

RegisterNetEvent("LSC-Sign")
AddEventHandler("LSC-Sign", function()
    TriggerServerEvent("QBCore:ToggleDuty")
end)

