all: feature_list.csv node_loc_list.csv fixed_data.csv

clean: 
	rm temp_*.txt

feature_list.csv: sensors.csv
	cat sensors.csv | cut -d "," -f  3,4 | sed 's/,/_/g' >$@

node_loc_list.csv: nodes.csv
	cat nodes.csv | sed 's/".*,.*"//g'| cut -f 1,5,6 -d ',' > $@

fixed_data.csv: new_data.csv
	cat new_data.csv | cut -f 1 -d "," > temp_timestamp.txt
	cat new_data.csv | cut -f 2 -d "," > temp_parameter.txt
	cat new_data.csv | cut -f 3 -d "," > temp_node_id.txt
	cat new_data.csv | cut -f 4 -d "," > temp_sensor.txt
	cat new_data.csv | cut -f 5 -d "," > temp_subsystem.txt
	cat new_data.csv | cut -f 8 -d "," > temp_value_hrf_avg.txt
	paste -d ',' temp_timestamp.txt temp_node_id.txt temp_subsystem.txt temp_sensor.txt temp_parameter.txt temp_value_hrf_avg.txt > $@
