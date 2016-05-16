#Objects
Config model contains different kind of static parameters.
    
    Config 
    {
        version         [text]
        server_ip       [text]
    }

##Pipelines

    Pipelines 
    {
        id              [key]
        name            [text]
        version         [text]
        description     [text]
        license         [text]
        homepage        [url]
        signature       [text]
      
    }

##Analysis

    Analysis 
    {
        id          [key]
        name        [string]
        author      [foreign_id]
        pipeline_id [foreign_id]
        
    }

##Users

    Users 
    {
        id              [key]
        username        [key]
        first_name      [String]
        second_name     [key]
    }

#ENDPOINT
##CONFIG
[GET] /config/

    Request:{}

    Response:
    { 
        version: "1.0",
        version_name: "Darwin"
    }

##Pipelines
[GET] /pipelines

    Request: 
    {
       limit: 10
    }

    Response:
    Body: 
    [{
        id: 34234324234
        name:"Wisecondor"
        version: "0.1"
        description: "trisomy detection pipeline"
        license:"GPL"
        homepage:"http://www.github.com/wisecondor"
        signature:"TC452GCG34223CCCGGG32324G"
    }]


[POST] /pipelines/upload
  
    Request / http multipart 
    {
        packageFiles
    }

    Response:{success:true}

[GET] /pipelines/{id}

    Request: {}
   
    Body: 
    {
        id: 34234324234
        name:"Wisecondor"
        version: "0.1"
        description: "trisomy detection pipeline"
        license:"GPL"
        homepage:"http://www.github.com/wisecondor"
        signature:"TC452GCG34223CCCGGG32324G"
    }


[DELETE] /pipelines/id
    
    Request: {}
    Response:{}

##Analysis

[GET] /analysis
    
    Request: {
        limit : 10
    }


    Response:
    [{
        id: 324234
        name:"Analyse de 4 patients"
        author: {
            username:"odnadna",
            first_name:"anne-sophie",
            last_name:"Denommé"
        }
        pipeline:{
            id: 34234324234
            name:"Wisecondor"
            version: "0.1"
            description: "trisomy detection pipeline"
            license:"GPL"
            homepage:"http://www.github.com/wisecondor"
            signature:"TC452GCG34223CCCGGG32324G" 
            config : {

            }
        }
    }]


[POST] /analysis/{id}
    
    Request: {
    }

    Response:
    {
        id: 324234
        name:"Analyse de 4 patients"
        author: {
            username:"odnadna",
            first_name:"anne-sophie",
            last_name:"Denommé"
        }
        pipeline:{
            id: 34234324234
            name:"Wisecondor"
            version: "0.1"
            description: "trisomy detection pipeline"
            license:"GPL"
            homepage:"http://www.github.com/wisecondor"
            signature:"TC452GCG34223CCCGGG32324G" 
            config : {
            }
        }
    }


[DELETE] /analysis/{id}
    
    Request: {}

    Response:{success:true}

[GET] /analysis/{id}
    
    Request: {}

    Response:
    {
        id: 324234
        name:"Analyse de 4 patients"
        author: {
            username:"odnadna",
            first_name:"anne-sophie",
            last_name:"Denommé"
        }
        pipeline:{
            id: 34234324234
            name:"Wisecondor"
            version: "0.1"
            description: "trisomy detection pipeline"
            license:"GPL"
            homepage:"http://www.github.com/wisecondor"
            signature:"TC452GCG34223CCCGGG32324G" 
            config : {
            }
        }
    }


#Summary 
* [GET] /config/
* [GET] /pipelines?limit=10
* [POST] /pipelines/upload/
* [GET] /pipelines/{id}
* [POST] /pipelines/{id}
* [DELETE] /pipelines/{id}

* [GET] /analysis?limit=10
* [GET] /analysis/{id}
* [POST] /analysis
* [DELETE] /analysis/{id}
* [GET] /analysis/{id}/status
* [GET] /analysis/{id}/files 

* [GET] /users?limit=10
* [GET] /users/{id}
* [POST] /users/
* [DELETE] /users/
* [PUT] /users/{id}
* [GET] /users/{id}/analysis











