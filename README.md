# Web service for A/B testing with CUPED
There is data on users and their purchases for 8 weeks. In the last week a series of experiments were conducted with the goal of increasing the average revenue per person. The task of the service is to determine if there is an effect or not <br/>

`main.ipynb` - main code file <br/>
`data_description.ipynb` - description of the source data <br/>
`checking_connection.ipynb` - code for checking readiness <br/>

`/ping` - for checking readiness <br/>
All data will be received and sent in json. <br/>
You can get it like this: `content = json.loads(request.json)`, where request is an object from `Flask library` <br/>

`/check_test` - evaluation of the pilot (accepts `POST` request), should return json where `has_effect=1` in case we think there is a positive effect, otherwise `has_effect=0` <br/>

`Query format` for `check_test:` a json query with three keys `['group_a_one', 'group_a_two', 'group_b']` whose values are a list of `user_id` users <br/>
`Example: {'test': {'group_a_one': [1, 2, 3], 'group_a_two': [4, 5, 6], 'group_b': [7, 8, 9]}}` <br/>
`Response format:` json with one `has_effect` field which takes values `0` and `1`