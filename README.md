## Moodle Question RestAPI
**Table of content:**

1. [Retrieve all nonempty contexts](#getcontexts)
2. [Retrieve all questions in a context](#retrieve_questions)
3. [Retrieve list of questions](#question_list)
4. [Answers](#answers)



###<a id="getcontexts"></a>Retrieve all nonempty contexts

|Request Method|Request Endpoint|
|--------------|----------------|
|GET           | /contexts      |


####Request Parameters
**None**
####Response Example:

```javascript
HTTP/1.1 200 OK
Content-Type:application/json;charset=UTF-8
{
	contexts: [
		{
			id:...,
			name:...,
			numquestions:...,
			numhidden:...
		},
		....
	]    
}
  	

```

###<a id="retrieve_questions"></a>Retrieve all questions in a context

|Request Method|Request Endpoint|
|--------------|----------------|
|GET           | /contexts/{context_id} |


####Request Parameters
**None**

####Response Example:

```javascript
HTTP/1.1 200 OK
Content-Type:application/json;charset=UTF-8
{
	questions: [
		{ 
			id:...,
			name:...,
			qtype:...
		},
		...
	]
}


```

###<a id="question_list"></a>Retrieve list of questions

|Request Method|Request Endpoint|
|--------------|----------------|
|GET           | /questions	    |


####Request Parameters
|Parameter|Description                     |
|---------|-----------                     |
|ids    |comma separated list of question ids|  

####Request Example:

```
/questions?ids=1,2,3
```

####Response Example:

```javascript
HTTP/1.1 200 OK
Content-Type:application/json;charset=UTF-8
{
	questions:[
		{
			name:...,
			text:...,
			id:...,
			type:...,
			answers:[] ***look in answers section for detailed description of answers object***
		},
	...
	]  
}
  	

```

###<a id="answers"></a>Answers
Answers is a list of answer objects. If it's empty this means that the question type doesn't support answers(open answer questions, etc.).
Example of answers:
```javascript
answers: [
	{
		text:...,
		format:... *** can be 0 or 1 still not shure will this property be included in the final version of the API***
	},
	...
	]
	
```
The documentation about answers is not ready yet. The way matching questions are going to be handled is still unclear.  