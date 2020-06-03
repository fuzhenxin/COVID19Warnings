# Introduction to the Data of COVID-19 Hazard Aera Warning System

### Raw Data
- data_raw.json is a list and each element of the list is a case of the confirmed cases for COVID-19 in China.
- Each case is in the format of [month, day, provience_name, city_name, district_name, [lng, lat]]
- Please note that the lat and lng are of [BD09](https://en.wikipedia.org/wiki/Restrictions_on_geographic_data_in_China#BD-09) coordinate system.
- After removing some noise cases, the raw data contains 15995 cases.

### Processed Data
- The Phase1, Phase2, Phase3 are in trainvalidtest.phase(1/2/3).json
- data structure:
```
[
    [EachCase, ...] # train
    [EachCase, ...] # valid
    [EachCase, ...] # test
]
EachCase = [month,day,provience_name, city_name, district_name, location_name, [lng,lat], FeatureDict]

FeatureDict = {"Geographical": ["lng", "lat", "nearest_x3", "kavg_x4", "inrange_x7", "region_nearest_x5", "region_mean_x6"],
           "Temporal": ["nearest_date_x15", "nearest_date_kmin_x16", "nearest_date_kmean_x17", "nearest_date_region_x18"],
           "Demographic": ["mall", "market", "hospital", "apartment", "metro", "population", "population density"],
           "Temperature": ["max", "min", "avg"],
           "LiveUpdate": ["local_confirm", "local_suspecte", "local_recover", "local_dead", "local_confirm_add",
                         "local_suspecte_add", "local_recover_add", "local_dead_add", "country_confirm",
                         "country_suspecte", "country_recover", "country_dead", "country_confirm_add",
                         "country_suspecte_add", "country_recover_add", "country_dead_add"],
           "Epidemiologica": ["local_diffusion", "local_dispersion", "local_growthrate", "local_doublingtime",
                                "country_diffusion", "country_dispersion", "country_growthrate", "country_doublingtime",
                                "local_r0", "country_r0", "local_beta", "local_gamma", "country_beta", "country_gamma"]}
```


### Acknowledgment
- http://lbsyun.baidu.com/
- https://m.mp.oeeee.com/h5/pages/v20/nCovcase/
- https://github.com/BlankerL/DXY-COVID-19-Data