
# Fall 2022 Web Dev Track <br />_Class Schedule and Materials_

Wednesday 6:30-9pm Section

[Development Environment Setup Instructions](https://github.com/CUNYTechPrep/guides#development-environment-setup)
___
## (8/31) Week 1

Lecture Slides 

[Week 1](https://docs.google.com/presentation/d/1x3ZgpUU78Szlv2MYEurGWT2MGifaogVynjpbzqjBofg/edit#slide=id.p)

Topics:
- Semester Overview
- Designing Web Apps
- Review: HTML & CSS
- Lab Bootstrap 5.2

Assignments:
- [Bootstrap Lab](https://github.com/CUNYTechPrep/lab-bootstrap-5.2)
    + Solution:
        + [General Solution](https://cunytechprep.github.io/lab-bootstrap-5-solution/)
        + [Alternating Solution](https://cunytechprep.github.io/lab-bootstrap-5-solution/alternating.html)
- **Project Ideation**: provide your idea in the [ideation document](https://docs.google.com/presentation/d/1E_I4xPxnGqlbCTZ0cBjCIN17-b2P7xjHbCG6_R1C4Js/edit#slide=id.gfe736c9b1a_0_136)
- Meet your classmates and **form teams**
    + Read through your classmates ideas and contact them over slack
    + Formed teams due in Week 3 class
___


## (9/7) Week 2

Lecture Slides:

[Week 2](https://docs.google.com/presentation/d/1hEk66SvgwV1oshPLHaDd5tstXcctox7v3hot399Qwa8/edit#slide=id.g4785ebae2a_0_77)

Topics:
- React Intro
- [React Intro code along](https://gist.github.com/medgardo/45d976f31c86bdc9928908bf46ca5393)
___


## (9/14) Week 3

Topics:

- [Client-Server Communication](https://docs.google.com/presentation/d/1hJgCCh3UiygFQ6q8_G7_KCn332rGuo6VPHlM49JM4Ao/edit#slide=id.p)
    + Parts of a URL
    + Understanding HTTP Request-Response
- [`fetch(...)` and Promises](https://docs.google.com/presentation/d/1ctGUH2sYpqDjo268t_nL0A3u1t6tzAqwk-mw5WIxwnM/edit#slide=id.p)
- More React
    + [Lab: React Toggle](https://github.com/CUNYTechPrep/lab-react-toggle)
    + [Lab: React Trivia](https://github.com/CUNYTechPrep/lab-react-trivia)

Assignments:
- [Submit Team Project Proposal](https://github.com/CUNYTechPrep/2022-fall-web-dev/blob/main/materials/team-project-proposal.md)
___


## (9/21) Week 4

Topics:
- More `fetch()` and React

Class Example:
```
function App() {
  const [data, setData] = useState([]);
  const [zipCode, setZipCode] = useState('');

  const fetchData = () => {
    fetch('https://ctp-zip-api.herokuapp.com/zip/' + zipCode , {
      'mode' : 'cors',
      headers: {
        'Content-Type' : 'application/json',
      }
    })
    .then((response) => response.json())
    .then((responseData) => setData(responseData))
    .catch((error) => console.log(error));
  }

  return (
    <div className="App">
      <div style={{marginTop: 20}}>
        <div>
          <input type="text" onChange={(e) => setZipCode(e.target.value)}></input>
        </div>
        <button onClick={() => fetchData(zipCode)}>Search</button>
        <pre>{JSON.stringify(data)}</pre>
      </div>
    </div>
  );
}
```

Assignments:
- [React Zip Code Search Lab](https://github.com/CUNYTechPrep/lab-react-zip-search)
___


## (9/28) Week 5

Topics:
- Fullstack Review: Frontend vs Backend
- About `npm`
- Building a backend with Express.js
  + Routing
  + Route Parameters
  + Query Parameters
  + Body Parameters
- RESTful Routing
___


## (10/5) NO CLASS
___


## (10/12) Week 6

Topics:
- SDLC (software development lifecycle)
- MVC (_Models-Views-Controllers_) Project Structure
- Databases and Data Modeling
- ORM's (Sequelize.js)

[CTP Design Doc Template](https://github.com/CUNYTechPrep/lab-react-zip-search)

___


## (10/19) Week 7

Topics:
- Using MVC app structure
- Project Starter setup and walkthrough
___


## (10/26) Week 8

Topics:
- Using Sequelize.js
- Testing (Jest)
___


## (11/2) Week 9

Topics:
- **_Project Presentations_**
- Implementing Authentication
- Sessions
- Passport.js, Bcrypt
___


## (11/9) Week 10

Topics:
- Code Reviews
- Software Engineering Best Practices
- [Resource link](http://web.mit.edu/6.005/www/fa16/classes/04-code-review/)
___


## (11/16) Week 11

Topics:
- Deploying to ~Heroku~ ??
- _Lab Time: Work on Projects_
___


## (11/23) NO CLASS
___


## Thanksgiving Break
___


## (11/30) Week 12

Topics:
- _Lab Time: Work on Projects_
___


## (12/7) Week 13
Topics:
- Practice Demo Night Pitches and Demos
- _Lab Time: Work on Projects_
___


## (12/14 - tentatively) DEMO NIGHT
___


### Demo Night
- Location: TBD
- Time: TBD
