## Week 10

# Task 9: Wildlife Module Get Surveys by Species

  Limitations : 
  
      •	The functions rely on external APIs which may have availability, rate limits, and performance limitations.
      •	The accuracy of data is dependent on the API's data, which may have inaccuracies or missing information.
      •	The filtering of incidental sightings assumes the presence of the SiteCode key in the survey data.

Code:
def search_sightings(taxonid, city):
    coordinate = gps_coordinate(city)
    cor = (0,0)
    if "latitude" in coordinate :
        cor = (coordinate["latitude"],coordinate["longitude"])
    
    #print(taxonid)
    surveys = get_surveys_by_species(cor, RADIUS, taxonid)
    #print(surveys)
    sightings = []
    #commenting following code as there are no records for incidental"
    """
    for survey in surveys:
        if "SiteCode" in survey and survey["SiteCode"] == "INCIDENTAL":
            sightings.append(survey)
    """
    return surveys

def get_surveys_by_species(coordinate, radius, taxonid):
    latitude, longitude = coordinate
    url = f"https://apps.des.qld.gov.au/species/?op=getsurveysbyspecies&taxonid={taxonid}&&circle={latitude},{longitude},{radius}"
    try:
        response = requests.get(url)
        response.raise_for_status()
        data = response.json()
        surveys = []
        if "features" in data:
            for feature in data["features"]:
                survey = feature["properties"]
                survey_data = {}
                survey_data["TaxonID"] = survey["TaxonID"]
                survey_data["StartDate"] = survey["StartDate"]
                survey_data["LocalityDetails"] = survey["LocalityDetails"]
                surveys.append(survey_data)
            
        return surveys
    except requests.exceptions.RequestException as e:
        print("Error connecting to wildlife data API:", e)
        return []
    except ValueError as e:
        print("Error parsing response from wildlife data API:", e)
        return []

