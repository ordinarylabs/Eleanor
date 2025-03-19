# Eleanor

Open, digital rolodex/social-trust graph protocol.

## Mission

Create a wiki-like experience for finding collaboration candidates, based on the word of people you already know, respect or trust.

## Viewer

A parser/viewer is likely something that will be worked on in the future. It would take a webpage like `https://yourpage.com`, check it for the `.well-known/trust-graph.json` path, and then render the properties it knows to account for as HTML, with all of the back-linked `"link"` properties validated and rendered either as "navigate to" or dropdown/pop-outs embedded in the core page. 

The viewer we build would be configurable and allow you to define which properties you want to include and how to display them, with templates.

## Audience

Engineers, artists, authors, tradespeople, builders, creators, etc.

## Format

The goal of this page is not to define a strict format or a single source of truth, but instead to start establishing a baseline mechanism for an open social-trust-graph protocol.

What an individual or organization decides to include as properties, or at what path, is up to them and what is most useful for their purposes.

Ideally, graph viewers would be flexible enough to account for many different configurations and structures. As each industry/subgroup/subgraph defines a more perfect structure for its needs (i.e Software Engineers may choose to include/exclude different properties than someone working in Marketing, or a Software Engineer lending expertise to tech-adjacent industries may include/exclude something different than an SWE who prefers to work mostly on SaaS products). 

### Individual

```jsonc
// https://yourpage.com/.well-known/trust-graph.json
{
    "i": {
        "name": "sam i am",
        // any extra attrs
        "dob": "12/24/1998",
        "contact": {
            "email": "samiam@yourpage.com",
        },
        "open-to": [
            "eating foods other than green eggs and ham"
        ],
        "skills": [
            // top level
            "not liking green eggs & ham",
            // nested
            "programming": [
                "javascript",
            ]
        ],
        "experiences": [
            {
                "title": "Green Eggs and Ham",
                "participation": "character in a story"
            }
        ],
        "organizations": [
            // can be "verified" by checking current address
            // is present on that page
            "https://yourorganizationpage.com/.well-known/trust-graph.json"
        ]
    },
    "trust": [
        {
            "name": "fox",
            "relationship": "fellow book character",
            "to": [
                "be in socks",
                // sub-category
                "home reno": [
                    // simple
                    "electrical",
                    // detailed
                    {
                        "task": "plumbing", 
                        "why": "fixed my sink twice" 
                    }
                ]
            ],
            "link": "https://handyfoxinsocks.com/.well-known/trust-graph.json"
        }
    ],
    "but-not": [
        {
            "name": "sam",
            "due-to": "continued pressuring to try foods which i do not like" 
        }
    ]
}
```

### Organization

```jsonc
// https://yourorganizationpage.com/.well-known/trust-graph.json
{
    "we": {
        "are": "book characters",
        "who": "do stuff"
    },
    "members": [
        {
            "name": "cat",
            "role": "hat wearer",
            "highlights": [
                "makes good trouble",
                "cleans up after self"
            ],
            "link": "https://messycatinthehat.com/.well-known/trust-graph.json"
        },
        {
            "name": "sam",
            "role": "food pressurer",
            "link": "https://samthegreenfoodie.com/.well-known/trust-graph.json"
        },
        {
            "name": "sam i am",
            "role": "food denier",
            "link": "https://yourpage.com/.well-known/trust-graph.json"
        }
    ]
}
```
