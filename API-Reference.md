> [Wiki](Home) ▸ **API Reference**

All the API below are accesible after creating an [instance of the lookup](Home#installing). The configuration functions are all getter-setter functions. The lookup components 

## [d3 (core)](Core)

### [[Configuration]]

* [[allowFreeTextInput|Configuration#allowFreeTextInput]] - get or set whether to enable entry of free text input
* [[focused|Configuration#focused]] - get or set whether the lookup is focused 
* [[label|Configuration#label]] - get or set the function used to interpret each data item
* [[loading|Configuration#loading]] - get or set the loading status of the lookup
* [[openOnStart|Configuration#openOnStart]] - get or start whether the options list should show when focused even when there is no input
* [[prompt|Configuration#prompt]] - get or set the placeholder text for the lookup
* [[query|Configuration#query]] - get or set the current text in the input of the lookup
* [[selected|Configuration#selected]] - get or set the selected options
* [[drawEmptyResults|Configuration#drawEmptyResults]] - get or set the function used to render the html when there are no results
* [[drawDropdownSuggestion|Configuration#drawDropdownSuggestion]] - get or set the function which renders each option
* [[filter|Configuration#filter]] - get or set the filter function which determines whether each option matches the given query
* [[groupingFunction|Configuration#groupingFunction]] - get or set the function which classifies the options into groups

### [[Events]]

* [[select|Events#select]] - triggered whenever the selected value of the lookup changes
* [[deselect|Events#deselect]] - triggered whenever a value is deselected or cleared
* [[input|Events#input]] - triggered whenever text is input
* [[focus|Events#focus]] - triggered whenever the lookup is focused