# Shared Housing Roommate Calculator -- Proof of Concept

This project is a Jupyter notebook (aka iPython).

## Using the notebook

The current iteration (as of this writing) _only does "hard" grouping_ -- identifying people who _cannot_ live together due to factors that are boolean. E.g., a person who can't live with dogs is not compatible with someone who owns a dog.

All inputs have been exeternalized to CSV files.

**DwellingSheet** expects two rows: a header row and a single unit. Currently the only hard-flag it has relates to offender status, which indicates whether it is too close to a school to accommodate certain offenders.

**HardFlagsSheet** expects a single row of hard-flag "roots", with no header row. The entry "dog" sets the expectation in the program that corresponding columns will be found in PeopleSheet: "dog_has" and "dog_conflict". If those columns are missing from PeopleSheet, the program will fail.

**PeopleSheet** is expected to contain data from both service providers and individuals seeking roommates. As stated above, columns must correspond correctly to the "roots" in the flags sheet. (Extra columns have no effect on the program.)

For each given root, two columns must exist:
* *<root>*_has -- ```y``` means person has that attribute.
* *<root>*_conflict -- ```y``` means person cannot live with someone with that attribute.

Care should be taken to validate that nonsense combinations of these paired columns aren't introduced into PeopleSheet, either in fake data (entered into csv) or by the eventual data entry app or survey form. For example, a person with ```dog_has``` set to ```y``` should not also have ```dog_conflict``` set to ```y```. (It may not behave unexpectedly, but it hasn't been tested. And besides, garbage is not good for algorithms anyway.)


