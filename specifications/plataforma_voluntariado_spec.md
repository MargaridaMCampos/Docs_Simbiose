**SIMBIOSE**

---
# Specification of `VOLUNTARIADO ÁGIL` platform

[ **TODO** - sacar um nome mais decente ]

* `version`: 0.1-beta
* `authors`: Margarida Campos, Emanuel Frazão, [mais!]
* `version start date`: 2022/01/21

---
---
# contents

1. [**introduction**](#introduction)
2. [**user requirements**](#user-requirements)
    1. [high view of the platform](#high-view-of-the-platform)
    1. [user types](#user-types)
        1. [external user](#external-user)
        1. [volunteer user](#volunteer-user)
        1. [institution user](#institution-user)
    1. [spaces](#spaces)
        1. [HOME](#home)
        1. [INITIATIVES](#initiatives)
        1. [IDEAS](#ideas)
        1. [PROFILES](#profiles)
        1. [DASHBOARD](#dashboard)
3. **functional requirements**
4. **software requirements**
5. **software architecture**
6. **implementation details**
7. **testing framework**
8. **plan and calendar**
9. [**references**](#references)

---
---
# introduction [$\uparrow$](#contents)

`Simbiose`'s primary goal is to *agilize voluntary work*.

There is currently no good and easy way for a wanna-be voluntary to find an institution in need - 
and there are plenty of wanna-be voluntaries, and plenty of institutions in need. `Simbiose` sees this as a gigantic flaw in the system, dragging only for our *still* immature usage of digital tools. [ TODO - ser muito menos dramático ]


`Simbiose` wants to solve this problem by creating a new *platform* of communication between `volunteers` and `institutions`. In creating this platform, we indeed hope to create a new *market* of cooperation: one that connects two entities absolutely complementary to each other and with a natural incentive to cooperate.

*(For accomplishing such graaand dreaaams!)* such a **platform** should:
* empower a wanna-be `volunteer` with:
    * the most frictionless way for finding 
    a project to work on,
    * a bird's eye-view on the variety of projects out there,
    * a validation of the `institution`s promoting the projects;
* and empower an `institution` with personel or material needs with:
    * a window for showcasing their projects and needs - with standardized support for marketing best practices,
    * a reference system for considering the `volunteer`s interested.

Furthermore, following `Simbiose`'s philosophy, the platform should be absolutely transparent regarding its usage and traffic.

---

The following chapters in this document detail the *software specificication* of the platform, starting by the *user requirements* - a formal yet undetailed description of what a user can expect to find in the platform.

---
---
# user requirements [$\uparrow$](#contents "Get back to contents.")

(See **user requirements**' diagram in [miro][pages-miro].)

## high view of the platform

From a high-view prespective, the platform is comprised of:
* 3 types of `users`:
    1. `external` user,
    1. `volunteer`,
    1. *non-profit* `institution`;
* 5 `spaces`, with permissions dependent on the user type:
    1. `HOME`, where everyone can find information on the platform and the description of each `space`,
    1. `INICIATIVES`, where each `institution` can create an `initiative` - for showcasing their needs and projects - for `volunteer`s to join,
    1. `IDEAS`, where each `volunteer` can propose an `idea` for a project - for some `institution` to later sponsor as an `initiative`,
    1. `PROFILES`, where each `institution` has its presentation page, and each `volunteer` has its basic history within the platform,
    1. `DASHBOARD`, where everyone can find statistics on the platform's trafic and usage data.

---
## user types
---
### external user

Any user that is not logged in is considered an `external` user.

#### permittable actions

An `external` user has access only to `HOME` and `DASHBOARD`, and is able to:
* at `HOME`:
    * see the same as any user (perhaps with some modifications);
* at `DASHBOARD`:
    * see the same as any user (without individual stats)

[ TODO - discutir tudo isto ]


---
### volunteer user

#### validation

Each volunteer *should* be validated directly, by requiring:
* *full name*,
* *age*,
* *id number*: cc/passport

In accepting to subscribe, the volunteer must get notified that any `institution` for which it works is entitled to ask to see the respective identification document.

#### permittable actions

A subscribed `volunteer` has access to all spaces, and is able to:
* at `HOME`:
    * see the same as any user;
* at `INITIATIVES`:
    * see all initiatives and search with full options functionality 
    * join an initiative,
* at `IDEAS`:
    * see all ideas and search with full options functionality
    * create/propose an idea
    * up-vote an idea
    * comment on an idea [ TODO - ver se faz sentido ]
* at `PROFILES`:
    * see every institution profiles
    * see its own profile
* at `DASHBOARD`:
    * see the same as any user


---
### institution user

#### validation

The validation of an `institution` will need revisiting and thorough addressing.




#### permittable actions


A validated `institution` has access to all spaces, and is able to:
* at `HOME`:
    * see the same as any user;
* at `INITIATIVES`:
    * see all initiatives and search with full options functionality,
    * create an initiative;
* at `IDEAS`:
    * see all ideas and search with full options functionality.
    * up-vote an idea,
    * sponsor an idea, i.e., turn it in an `initiative`;
* at `PROFILES`:
    * see every institution profiles
    * see every volunteer profiles
    * update its own profile
* at `DASHBOARD`:
    * see the same as any user


---
## spaces
---
### HOME

* login/sign up

---
### INITIATIVES

The `INITIATIVES` space holds the collection of all iniciatives - each represented as an `iniciative card` - with options for different visualization modes and filtering. It is the space where an `institution` can create a new `iniciative` and a `volunteer` may join any of them.

#### iniciative card

An `iniciative card` is the atomic constituent of `INITIATIVES` space and has the following attributes:
* (required) `name` of the initiative, which must be unique with respect to the `institution`'s past initiatives;
* (required) `institution` creating the initiative;
* (required) `mode`, which can fall into:
    * *personel*, further subdivided into:
        * *presential*,
        * *remote*;
    * *material*;
* (required) `categories`, the collection of categories, where each must be hierarchical (e.g., social/cooking, social/education/mathematics)
* (required) `date`, which can have the formats:
    * *finite*, for when it has a specific set of dates,
    * *continuous*, for when it is an on-going project - further subdivided into:
        * *sporadic*,
        * *regular*;
* (optional) `location` at which it takes place, if applicable;
* (required) `short description` of the initiative 
* (required) `full description`, which *should* follow certain guidelines - suggested when an `institution` is creating an initiative;
* (required) `image`, which might be:
    * uploaded by the `institution`,
    * chosen by the `institution` from a given bank of images,
    * the default - the `institution`'s presentation image.
* (required) `status`, which can fall into:
    * *open*
    * *closed*


An `initiative card` can then appear with different levels of information (depending on the `visualization mode` of `INITIATIVES`):
* *full information*: in which all attributes are displayed;
* *card information*: in which the attributes displayed are:
    * `name`
    * `institution`
    * `short description`
    * `date`
    * `location`
    * `status`
* *timeline information*: in which 
    * ``
* *map information*: in which the attributes displayed are:
    * `name`
    * `location`
    * `status`

 [ TODO - discutir tudo isto ]

---
#### visualization modes

The `initiative cards` must be possible to visualize in the following modes:
* `grid`, the default mode, in which:
    * all `cards` are arranged in a grid-like manner [ TODO - discutir infinite scroll vs pages ]
    * each `card` appears represented with *reduced information*
* `time-line`, in which:
    * one is to select a time range, 
    * `cards` appear in a sequential order wrt time
    * `cards` that overlap in time appear in paralel
    * each `card` appears represented with *timeline information*
* `map`, in which:
    * one has access to a map,
    * each `card` appears as a small icon at their `location`
* `single initiative`, the view for full information on the `card`

[ TODO - discutir também isto ]

---
#### filtering options

Every user with access to `INITIATIVES` should have the following filtering options:
* in every visualization mode:
    * by `name`
    * by `institution`
    * by `category`:
        * hierarchical
    * by `status`
* if not in `map` mode:
    * by `location`
* if not in `time-line` mode:
    * by `date`

---
#### creating an initiative

---
#### joining an initiative
    

---
### IDEAS

---
### PROFILES

---
### DASHBOARD


---
---
# references [$\uparrow$](#contents "Get back to contents.")


[pages-miro]: https://miro.com/app/board/o9J_lbOC5uo=/ "Home of Simbiose's `miro` board."

* `Miro` [home page][pages-miro]


