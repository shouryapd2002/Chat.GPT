# Chat.GPT
AI Chat Bot//Reinforcement Learning
User Story
So let us start by asking ChatGPT to respond to a user story.


As you can see, this user story is specific to my industry. ChatGPT has a vast knowledge base, so experimentation is required to understand ChatGPT's depth of knowledge — what does it know?

The key here with the initial question is to be very explicit about crucial details to get the best results. This way, ChatGPT can respond with a decent set of results such as this:


If your results are anything like the above, then you know that ChatGPT has picked up the trail and will build on further questions you ask. The key to remember is that all the following results will be based on this initial context, hence why it is worth spending time defining the first interaction well.

So now we can do something rather remarkable. Build a database!

Let's Make a Database

… and this is how ChatGPT responds:


But let's not stop there. Let's continue…


CREATE TABLE Surveyors (
    id INT NOT NULL AUTO_INCREMENT,
    name VARCHAR(255) NOT NULL,
    email VARCHAR(255) NOT NULL,
    password VARCHAR(255) NOT NULL,
    PRIMARY KEY (id)
);

CREATE TABLE Buildings (
    id INT NOT NULL AUTO_INCREMENT,
    type_id INT NOT NULL,
    coordinates VARCHAR(255) NOT NULL,
    notes TEXT,
    surveyor_id INT NOT NULL,
    PRIMARY KEY (id),
    FOREIGN KEY (type_id) REFERENCES BuildingTypes(id),
    FOREIGN KEY (surveyor_id) REFERENCES Surveyors(id)
);

CREATE TABLE BuildingTypes (
    id INT NOT NULL AUTO_INCREMENT,
    type VARCHAR(255) NOT NULL,
    PRIMARY KEY (id)
);
… to which ChatGPT responds with perfectly acceptable SQL, which SQL database will have no problem creating. However, let's not stop there again…

Creating Diagrams

<script src="https://cdn.jsdelivr.net/npm/mermaid@8.6.0/dist/mermaid.min.js"></script>
<script>mermaid.initialize({startOnLoad:true});</script>

<div class="mermaid">
    classDiagram
    class Surveyors {
        +id: int
        +name: string
        +email: string
        +password: string
    }
    class Buildings {
        +id: int
        +type_id: int
        +coordinates: string
        +notes: string
        +surveyor_id: int
    }
    class BuildingTypes {
        +id: int
        +type: string
    }
    Surveyors --> Buildings
    Buildings --> BuildingTypes
</div>
The diagram ChatGPT produces looks like this …


ChatGPT is full of surprises:



ChatGPT will not display diagrams but generate the code in Mermaid script, which will create the diagrams. ChatGPT is fully conversant with Mermaid script, so it can produce diagrams that this scripting language will allow.

As we've established, ChatGPT has been taught to code, so you can continue to ask ChatGPT to write JavaScript, CSS, and HTML to put a working prototype together by simply asking for it. ChatGPT has been trained to generate code in many popular programming languages.

Given enough time, this is something a skilled person could do. Granted, but more slowly. But this is something other than production-ready code; much more work is required to get the code to that level of quality and usefulness. But there is no reason why ChatGPT shouldn't sit idly by whilst doing that.

So let us try to improve the quality of the code using ChatGPT:


This is how ChatGPT responded:

public class Surveyor
{
    private readonly string _name;
    private readonly string _email;
    private readonly List<ISurvey> _surveys;
    private readonly IDatabaseAccess _databaseAccess;

    public Surveyor(string name, string email, IDatabaseAccess databaseAccess)
    {
        _name = name;
        _email = email;
        _databaseAccess = databaseAccess;
        _surveys = new List<ISurvey>();
    }

    public void AddSurvey(ISurvey survey)
    {
        try
        {
            _surveys.Add(survey);
            _databaseAccess.SaveSurvey(survey);
        }
        catch (Exception ex)
        {
            // Log the error
        }
    }

    public void RemoveSurvey(ISurvey survey)
    {
        try
        {
            _surveys.Remove(survey);
            _databaseAccess.DeleteSurvey(survey);
        }
        catch (Exception ex)
        {
            // Log the error
        }
    }

    public List<ISurvey> GetSurveys()
    {
        try
        {
            return _databaseAccess.GetSurveys();
        }
        catch (Exception ex)
        {
            // Log the error
            return new List<ISurvey>();
        }
    }
}

public interface IDatabaseAccess
{
    void SaveSurvey(ISurvey survey);
    void DeleteSurvey(ISurvey survey);
    List<ISurvey> GetSurveys();
}

public class DatabaseAccess : IDatabaseAccess
{
    public void SaveSurvey(ISurvey survey)
    {
        // Implementation for saving the survey to a database
    }

    public void DeleteSurvey(ISurvey survey)
    {
        // Implementation for deleting the survey from the database
    }

    public List<ISurvey> GetSurveys()
    {
        // Implementation for retrieving a list of surveys from the database
    }
}

public interface ISurvey
{
    decimal Latitude { get; set; }
    decimal Longitude { get; set; }
    string BuildingType { get; set; }
    Dictionary<string, string> BuildingCharacteristics { get; set; }
}

public class Survey : ISurvey
{
    public decimal Latitude { get; set; }
    public decimal Longitude { get; set; }
    public string BuildingType { get; set; }
    public Dictionary<string, string> BuildingCharacteristics { get; set; }

    public Survey(decimal latitude, decimal longitude, string buildingType, Dictionary<string, string> buildingCharacteristics)
    {
        Latitude = latitude;
        Longitude = longitude;
        BuildingType = buildingType;
        BuildingCharacteristics = buildingCharacteristics;
    }
}
… which as a set of classes to get things started is somewhat respectable.

The next task I got ChatGPT to do was to create the Swagger for a REST-based API. Again ChatGPT returns a respectable effort that is enough to get development started.


Conclusion
ChatGPT can start development as it has the breadth of power but has yet to show the depth. At each turn, I've had to provoke ChatGPT to do the task; there is no initiative there, and I have initiated and driven the next steps.

However, developing a standard set of questions that you know will provoke ChatGPT into delivering a good result could be straightforward. This may be enough in sprint planning to start development in many ways.

This technology is now here, and we may as well fully embrace it and continue to experiment so we can further understand what value this advanced automation can continue to provide.
