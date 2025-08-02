# Context Protocol for LLM

This document provides a comprehensive overview of the Narrative Context Protocol (NCP) for optimal use with a Large Language Model.

## 1. Introduction to the Narrative Context Protocol (NCP)

The **Narrative Context Protocol (NCP)** is an open, standardized JSON schema designed to transport and preserve **authorial intent** across diverse multi-agent storytelling systems. Its primary purpose is to reliably capture and convey narrative context, artistic voice, and thematic coherence across various platforms and autonomous agents.

### Core Philosophy: Subtext vs. Storytelling

NCP is built on a fundamental distinction between two layers of narrative design:

-   **Subtext**: Represents the deeper, intended meaning crafted by the author. It is the underlying thematic structure and ensures the story's core message remains consistent.
-   **Storytelling**: Represents the adaptable, creative presentation of the subtext to an audience. It is how the story is told and can be modified for different mediums and styles without losing the author's original intent.

This separation allows for both narrative depth and creative flexibility. It ensures that even as a story is extended or adapted by multiple agents or systems, its logical consistency and emotional core remain intact. NCP acts as a "blockchain-for-subtext," transparently tracking contributions and ensuring the original author's vision is respected and traceable.

## 2. Core Concepts

The NCP schema organizes a narrative into a clear hierarchy.

### Story

The `Story` is the highest-level object. It contains all metadata for the entire narrative, such as its ID, title, genre, and logline, and holds one or more `Narrative` objects.

### Narrative

A single story can contain multiple narratives (e.g., a main plot and a subplot). Each `Narrative` object is divided into the two core layers: `Subtext` and `Storytelling`.

### Subtext: The Narrative's Meaning

Subtext contains the structural components that define the author's intent and the story's deeper meaning.

-   **Perspectives**: These are the authorial viewpoints or lenses through which the story's conflict is explored (e.g., Main Character, Objective Story). They allow the author to assign thematic arguments to different viewpoints, enriching the narrative.
-   **Players**: These are the characters within the story, defined by their narrative roles and functions that advance the plot and reinforce themes.
-   **Dynamics**: These are high-level narrative forces that shape the story's structural framework and encode the author's intended message (e.g., Story Outcome: Success/Failure).
-   **Storypoints**: These are key thematic concepts and structural ideas (e.g., Problem, Solution, Goal). They represent the spatial, foundational arrangement of the narrative.
-   **Storybeats**: These are temporal elements that map the chronological progression of the story. They mark significant shifts in thematic exploration and character development.

### Storytelling: The Narrative's Presentation

Storytelling contains the audience-facing elements that shape how the story is experienced.

-   **Overviews**: These are high-level summaries and descriptions, such as throughlines, plot summaries, and character arcs, that give a clear understanding of the narrative's direction.
-   **Moments**: These are organizational units like acts, scenes, or chapters. They structure the narrative flow and include synopses and references to the underlying `Storybeats`.

## 3. Schema Overview

The following is a simplified, human-readable overview of the NCP JSON schema structure.

-   **story**: The root object.
    -   `id` (string): Unique identifier for the story.
    -   `title` (string): The title of the story.
    -   `genre` (string): The genre.
    -   `logline` (string): A short summary of the story.
    -   `created_at` (string): Creation timestamp.
    -   `narratives` (array): An array containing one or more `narrative` objects.
        -   **narrative**: Represents a single narrative thread.
            -   `id` (string): Unique identifier for the narrative.
            -   `title` (string): The title of the narrative.
            -   `subtext` (object): Contains the core meaning.
                -   `perspectives` (array of objects): The authorial viewpoints.
                    -   `id`, `author_structural_pov`, `summary`, `storytelling`
                -   `players` (array of objects): The characters.
                    -   `id`, `name`, `role`, `visual`, `audio`, `summary`, `storytelling`, `perspectives`
                -   `dynamics` (array of objects): The high-level narrative forces.
                    -   `id`, `dynamic`, `vector`, `summary`, `storytelling`
                -   `storypoints` (array of objects): The spatial thematic elements.
                    -   `id`, `appreciation`, `method`, `illustration`, `summary`, `storytelling`, `perspectives`
                -   `storybeats` (array of objects): The temporal thematic elements.
                    -   `id`, `appreciation`, `sequence`, `method`, `illustration`, `summary`, `storytelling`, `tones`, `perspectives`
            -   `storytelling` (object): Contains the presentation elements.
                -   `overviews` (array of objects): High-level summaries.
                -   `moments` (array of objects): Organizational units (scenes, acts).
                    -   `id`, `summary`, `synopsis`, `setting`, `timing`, `storybeats` (references)

## 4. Terminology

This section provides the official vocabulary for the Narrative Context Protocol.

### 4.1 Perspectives

Perspectives define the authorial viewpoints from which a story is told.

-   **Objective Story Throughline (`they`)**: The central, overarching conflict of the story.
-   **Main Character Throughline (`i`)**: The personal, internal conflict and baggage of the Main Character.
-   **Catalyst Provocateur Throughline (`you`)**: The perspective that challenges and provokes growth in the Main Character.
-   **Relationship Story Throughline (`we`)**: The perspective focused on the growth and dynamics of a key relationship.

### 4.2 Appreciations of Narrative

Appreciations are how we interpret and appreciate narrative conflicts. They are formed by pairing a Perspective with a Storypoint or Storybeat.

-   **Objective Story Adjustment**: what alters the course for those involved in the Objective Story Throughline; an indication of self-actualization.
-   **Objective Story Benchmark**: the standard by which progress is measured in the Objective Story.
-   **Objective Story Catalyst**: the item whose presence always pushes the Objective Story forward.
-   **Objective Story Condition**: the essence of inequity in the Objective Story Throughline.
-   **Objective Story Direction**: the direction of efforts in the Objective Story.
-   **Objective Story Facet**: the issue of greatest thematic focus within the Objective Story Throughline.
-   **Objective Story Field**: the area of concern for everyone in the Objective Story Throughline.
-   **Objective Story Flow**: the adaptive response to narrative challenges, where characters navigate obstacles by embracing flexibility and seeking creative solutions within the Objective Story Throughline.
-   **Objective Story Focus**: where attention is focused in the Objective Story.
-   **Objective Story Form**: the general area of conflict as it applies to everyone in the Objective Story Throughline.
-   **Objective Story Inhibitor**: the item that impedes the Objective Story's progress.
-   **Objective Story Problem**: the source of conflict within the Objective Story Throughline.
-   **Objective Story Resistance**: the collective obstacles and challenges that arise from the story's conditions, hindering the characters' progress towards their shared goals.
-   **Objective Story Solution**: the quality necessary to resolve the Objective Story Throughline's Problem.
-   **Story Consequence**: the area that best describes the result of failing to achieve the Story Goal.
-   **Story Costs**: the area that best describes the costs incurred while trying to achieve the goal.
-   **Story Dividends**: the area that best describes the dividends accrued while trying to achieve the goal.
-   **Story Ennui**: the emotional stagnation that signals the approach of Overwhelm.
-   **Story Excitement**: the positive vibrations that energize the Storymind and indicate the positive benefits of the journey.
-   **Story Forewarnings**: the area that best describes the imminent approach of the story consequences.
-   **Story Goal**: the common goal of the Objective Story Players.
-   **Story Habituations**: the systems or routines that align the Storymind with its Intention.
-   **Story Intention**: the directed intention of the Main Character's growth.
-   **Story Internalizations**: the self-awareness and introspection necessary for Habituation.
-   **Story Overwhelm**: the area that best describes the area where a sense of overwhelm resides.
-   **Story Preconditions**: the area that best describes the conditions imposed on meeting the Story Requirements.
-   **Story Prerequisites**: the area that best describes what is needed to meet the Story Requirements.
-   **Story Pressure**: the emotional and spiritual strain that challenges the Storymind.
-   **Story Requirements**: the area that best describes the requirements that must be met prior to achieving the Story Goal.
-   **Story Socializations**: the developing of relationships and social/emotional aspects as a means to foster support for the act of internalization.
-   **Main Character Adjustment**: the counterweight and shift in equilibrium that alters the Main Character's personal journey, and steers them down a new path.
-   **Main Character Baseline**: the specific element that defines the initial baseline motivation behind the Main Character's unique point-of-view.
-   **Main Character Benchmark**: the nature of the Main Character's effort to solve his personal problem; the standard by which the Main Character judges the degree of his concern.
-   **Main Character Condition**: the source of the Main Character's personal inequity, driving their growth and journey along their path of self-actualization.
-   **Main Character Critical Flaw**: the quality that undermines the Main Character's efforts.
-   **Main Character Direction**: the efforts of the Main Character to solve his apparent problems.
-   **Main Character Evolution**: the specific element that defines the evolved motivation of the Main Character's unique point-of-view.
-   **Main Character Facet**: the thematic focus, topic, or value standard addressed in the Main Character Throughline.
-   **Main Character Field**: the primary type of conflict found within the Main Character's personal Throughline.
-   **Main Character Flow**: the Main Character's adaptive approach and resilience in overcoming obstacles, facilitating their journey towards personal growth and self-actualization.
-   **Main Character Focus**: where the Main Character believes the problem to be; where the Main Character's attention is focused.
-   **Main Character Form**: the general area of conflict for the Main Character.
-   **Main Character Introduction**: the initial state or starting point of the Main Character's journey.
-   **Main Character Pivotal Element**: the specific element that ties the Main Character to the plot of the story.
-   **Main Character Problem**: the source of the Main Character's motivations and/or problems.
-   **Main Character Resistance**: the perceived obstacle or challenge that hinders the Main Character's personal growth and self-actualization.
-   **Main Character Resolution**: the final state or conclusion of the Main Character's journey.
-   **Main Character Solution**: what is needed to truly satisfy the Main Character's motivation, or the solution to the Main Character's problems.
-   **Main Character Unique Ability**: the quality that makes the Main Character uniquely qualified to solve the story's problem/achieve the goal.
-   **Catalyst Provocateur Adjustment**: the counterweight and shift in equilibrium that alters the Catalyst Provocateur's influence on the Main Character's personal journey, acting as a catalyst for realignment and steering the Main Character towards a new path.
-   **Catalyst Provocateur Baseline**: the specific element that defines the initial motivation behind the Influence Character's unique point-of-view.
-   **Catalyst Provocateur Benchmark**: the standard against which the Catalyst Provocateur's concern is measured.
-   **Catalyst Provocateur Condition**: the source of the Catalyst Provocateur's influence on the Main Character's personal growth and journey, guiding and aligning them along their path of self-actualization.
-   **Catalyst Provocateur Critical Flaw**: the item that undermines the Catalyst Provocateur's efforts.
-   **Catalyst Provocateur Direction**: the direction of the Catalyst Provocateur's efforts.
-   **Catalyst Provocateur Evolution**: the specific element that defines the evolved motivation of the Catalyst Provocateur's unique point-of-view.
-   **Catalyst Provocateur Facet**: the specific issue that best describes the influence the Catalyst Provocateur has on the Main Character.
-   **Catalyst Provocateur Field**: the type of impact the Catalyst Provocateur has over the Main Character.
-   **Catalyst Provocateur Flow**: the dynamic engagement by the Catalyst Provocateur that amplifies their Resistance, further encouraging the Main Character to question and reassess their personal justifications.
-   **Catalyst Provocateur Focus**: where the Catalyst Provocateur's attention is most directed.
-   **Catalyst Provocateur Form**: the shape of conflict found from the Catalyst Provocateur point-of-view.
-   **Catalyst Provocateur Introduction**: the initial state or starting point of the Catalyst Provocateur's journey.
-   **Catalyst Provocateur Pivotal Element**: the specific element that ties the Catalyst Provocateur to the plot of the story.
-   **Catalyst Provocateur Problem**: the source of the Catalyst Provocateur's drive.
-   **Catalyst Provocateur Resistance**: the manner in which the Catalyst Provocateur challenges and disrupts the Main Character's personal beliefs and justifications, serving as a catalyst for introspection and change.
-   **Catalyst Provocateur Resolution**: the final state or conclusion of the Catalyst Provocateur's journey.
-   **Catalyst Provocateur Solution**: what is needed to truly satisfy the Catalyst Provocateur's motivation.
-   **Catalyst Provocateur Unique Ability**: the item that makes the Catalyst Provocateur uniquely able to thwart the Main Character.
-   **Relationship Story Adjustment**: the specific element that shifts the nature of the relationship between the principle characters.
-   **Relationship Story Benchmark**: the standard by which growth is measured in the Relationship Story Throughline.
-   **Relationship Story Catalyst**: the item that acts as the catalyst to move the Relationship Story Throughline.
-   **Relationship Story Condition**: the underlying condition for the relationship between the principle characters.
-   **Relationship Story Direction**: The direction of efforts in the Relationship Story Throughline; the apparent remedy for the symptom of the difficulties between the Main Character and the Impact Character.
-   **Relationship Story Facet**: the thematic focus, or value standard, measured within the Relationship Story Throughline.
-   **Relationship Story Field**: the area of concern within the relationship featured in the Relationship Story Throughline.
-   **Relationship Story Flow**: the adaptive dynamics within the relationship between the principal characters that overcome resistance and foster growth.
-   **Relationship Story Focus**: the principal symptom of the difficulties between the Main Character and the Impact Character, where attention is focused in the Relationship Story Throughline.
-   **Relationship Story Form**: the general area of growth in the Relationship Story Throughline.
-   **Relationship Story Inhibitor**: the item that impedes growth in the Relationship Story Throughline.
-   **Relationship Story Problem**: the underlying cause of the difficulties between the Main Character and the Impact Character.
-   **Relationship Story Resistance**: the resistance towards growth found in the relationship between the principle characters.
-   **Relationship Story Solution**: the specific element needed to resolve the difficulties between the Main Character and the Impact Character.

### 4.3 Methods of Conflict

Methods are the small narrative "engines" that process and navigate conflict.

-   **Ability**: being suited to handle a task; the innate capacity to do or be.
-   **Able**: being inherently capable of action or adaptation.
-   **Acceptance**: a decision to allow.
-   **Accurate**: being within tolerances.
-   **Actuality**: an objective reality of the way things are.
-   **Altruism**: doing or being based on what is best for others.
-   **Analysis**: evaluation of the situation and/or circumstances.
-   **Appraisal**: an initial understanding.
-   **Approach**: one's methodology of doing or being.
-   **Attempt**: applying oneself to something not known to be within one's ability.
-   **Attitude**: one's demeanor while doing or being.
-   **Attraction**: drawing or being drawn to something.
-   **Avoid**: stepping around, preventing or escaping from a problem rather than solving it.
-   **Aware**: being conscious of things outside oneself.
-   **Becoming**: transforming one's nature.
-   **Being**: temporarily adopting a lifestyle.
-   **Cause**: the specific circumstances that lead to an effect.
-   **Certainty**: a conclusion that something is absolutely true.
-   **Change**: an alteration of a state or process.
-   **Chaos**: random change or a lack of order.
-   **Choice**: making a decision.
-   **Circumstances**: the relationship of oneself to the environment.
-   **Closure**: bringing something to an end.
-   **Commitment**: a decision to stick with something regardless of the consequences.
-   **Conceiving**: coming up with an idea.
-   **Conceptualizing**: visualizing how an idea might be implemented.
-   **Conditioning**: responses based on experience or training.
-   **Confidence**: belief in the accuracy of an expectation.
-   **Conscience**: forgoing an immediate benefit because of future consequences.
-   **Conscious**: considerations.
-   **Consider**: weighing pros and cons.
-   **Continuing**: a process of sustained progression and ongoing engagement.
-   **Control**: a method based on organization and constraint.
-   **Deduction**: a process of thought that determines certainty.
-   **Deficiency**: motivation based on lack.
-   **Delay**: putting off until later.
-   **Denial**: the refusal to let something go.
-   **Desire**: the motivation to change one's situation or circumstances.
-   **Destiny**: the future path an individual will take.
-   **Determination**: a conclusion as to the cause behind a particular effect.
-   **Deviation**: not within tolerances.
-   **Disbelief**: the belief that something is untrue.
-   **Doing**: engaging in a physical activity.
-   **Doubt**: questioning validity without investigating to be sure.
-   **Dream**: a desired future that requires unexpected developments.
-   **Driven**: being internally compelled toward change or fulfillment.
-   **Effect**: the specific outcome forced by a cause.
-   **Ending**: coming to a conclusion.
-   **Enlightenment**: an understanding that transcends knowledge.
-   **Equity**: a balance, fairness, or stability.
-   **Evaluation**: an appraisal of a situation and/or circumstances.
-   **Evidence**: information supporting a belief.
-   **Expectation**: a conclusion as to the eventual effect of a particular cause.
-   **Expediency**: most efficient course considering repercussions.
-   **Experience**: the gaining of familiarity.
-   **External Framing**: seeing problems and inequity through the lens of a fixed external state.
-   **External Processing**: seeing problems and inequity through the lens of an external process of activity.
-   **Fact**: belief in something real.
-   **Faith**: accepting something as certain without proof.
-   **Falsehood**: that which has been shown to be erroneous.
-   **Fantasy**: belief in something unreal.
-   **Fate**: a future situation that will befall an individual.
-   **Feeling**: an emotional sense of how things are going.
-   **Free**: a method characterized by liberation and expansive, spontaneous expression.
-   **Future**: what will happen or what will be.
-   **Help**: a direct assistance to another's effort to achieve their goal.
-   **Hinder**: a direct detraction from another's effort to achieve their goal.
-   **Hope**: a desired future if things go as expected.
-   **Hunch**: a conclusion based on intuition.
-   **Inaction**: taking no action as a means of response.
-   **Induction**: a means of determining possibility.
-   **Inequity**: an unbalance or unfairness, or a lack of stability.
-   **Inertia**: a continuation of a state or process.
-   **Instinct**: intrinsic unconditioned responses.
-   **Interdiction**: an effort to change a pre-determined course.
-   **Internal Framing**: seeing problems and inequity through the lens of a fixed internal state.
-   **Internal Processing**: seeing problems and inequity through the lens of an internal process of thinking.
-   **Interpretation**: determination of possible meaning.
-   **Investigation**: gathering evidence to resolve questions of validity.
-   **Knowing**: being in a state of assumed truth.
-   **Knowledge**: that which one holds to be true.
-   **Learning**: gathering information or experience.
-   **Logic**: a rational sense of how things are related.
-   **Memory**: recollections.
-   **Need**: that which is required.
-   **Obligation**: accepting a task or situation in exchange for someone's potential favors.
-   **Obtaining**: achieving or possessing something.
-   **Openness**: willingness to re-evaluate.
-   **Oppose**: an indirect detraction from another's effort.
-   **Order**: an arrangement in which patterns are seen.
-   **Past**: what has already happened.
-   **Perception**: the way things seem to be.
-   **Permission**: one's ability based on what is allowed.
-   **Possibility**: a determination that something might be true.
-   **Potentiality**: a determination that something has the capacity to become true.
-   **Preconception**: unwillingness to re-evaluate.
-   **Preconscious**: immediate responses.
-   **Prediction**: a determination of a future state of affairs.
-   **Present**: the current situation and circumstances.
-   **Presumption**: a rating of knowledge that has not been tested.
-   **Proaction**: taking initiative action to achieve one's goals.
-   **Probability**: a determination of likelihood.
-   **Process**: the mechanism through which a cause leads to an effect.
-   **Production**: a process of thought that determines potential.
-   **Progress**: the way things are going.
-   **Projection**: an extension of probability into the future.
-   **Protection**: an effort to prevent one's concerns from being vulnerable to interference.
-   **Proven**: a rating of knowledge based on corroboration.
-   **Pursuit**: a directed effort to resolve a problem.
-   **Qualification**: critical criteria to be fulfilled.
-   **Rationalization**: a logical alternative used to mask the real reason.
-   **Re-evaluation**: a reappraisal of a situation or circumstances.
-   **Reaction**: actions made in response.
-   **Reappraisal**: a reconsideration of a conclusion.
-   **Reconsider**: questioning a conclusion based on additional information.
-   **Reduction**: a process of thought that determines probability.
-   **Rejection**: a decision to oppose.
-   **Repulsion**: pushing or being pushed away from.
-   **Responsibility**: the belief that one is best suited to accomplish a task.
-   **Result**: the ramifications of a specific effect.
-   **Security**: an evaluation of one's protections.
-   **Self Interest**: doing or being based on what is best for oneself.
-   **Self-aware**: being conscious of one's own existence.
-   **Sense of Self**: one's perception of oneself.
-   **Senses**: sensory observations.
-   **Situation**: the arrangement of one's environment.
-   **Skill**: practiced ability.
-   **Speculation**: an extension of possibilities into the future.
-   **State of Being**: one's true nature.
-   **Stipulation**: imposed limitations or conditions tacked on to an effort.
-   **Strategy**: a plan to achieve one's purpose or a plan of response.
-   **Subconscious**: basic drives and desires.
-   **Support**: an indirect assistance given to another's efforts.
-   **Suspicion**: questioning a belief based on evidence.
-   **Temptation**: the urge to embrace immediate benefits despite possible consequences.
-   **Test**: a trial to determine something's validity.
-   **Theory**: an unbroken chain of relationships leading from a premise to a conclusion.
-   **Thinking**: being in a state of mental exploration.
-   **Thought**: the process of consideration.
-   **Threat**: an evaluation of one's vulnerabilities.
-   **Trust**: an acceptance of knowledge as proven without first testing its validity.
-   **Truth**: that which has been proven correct.
-   **Understanding**: appreciating the meaning of something.
-   **Value**: the objective usefulness or desirability of something in general.
-   **Wisdom**: understanding how to apply knowledge.
-   **Work**: applying oneself to something known to be within one's ability.
-   **Worry**: concern for the future.
-   **Worth**: a rating of usefulness or desirability to oneself.

### 4.4 Dynamics

Dynamics are high-level narrative forces that shape the story's message and structure.

-   **Main Character Resolve**: the way in which the Main Character ultimately deals with conflict.
-   **Catalyst Provocateur Resolve**: the degree to which the Catalyst Provocateur feels compelled to remain on the quest.
-   **Main Character Growth**: the direction the Main Character grows in their attempt to resolve their personal inequities.
-   **Main Character Approach**: the Main Character's preferred method of resolving their personal baggage.
-   **Narrative Alignment**: a determination of the narrative's operating system as reflected in the Main Character.
-   **Narrative Fabric**: the nature of the sequence of events in a story.
-   **Story Driver**: the kind of activity focused upon in the effort to resolve the story's conflict.
-   **Ending**: in a dopamine-aligned narrative, the meaningful conclusion to the narrative.
-   **Attunement**: in a serotonin-aligned narrative, the meaningful path the narrative takes.
-   **Story Outcome**: an objective assessment of how things ended up in the Objective Story Throughline.
-   **Story Judgment**: the author's assessment of whether or not the Main Character has resolved their personal baggage.
-   **Story Balance**: the equilibrium of forces at play as the story pivots toward a new direction.
-   **Story Vibes**: the sense of whether the Main Character is moving up or sliding down the emotional ladder.

### 4.5 Vectors

Vectors indicate the narrative direction taken by Dynamics, often representing a binary choice.

-   **Relinquished**: abandoning a point-of-view.
-   **Maintained**: sticking with a point-of-view.
-   **Released**: letting go a point-of-view.
-   **Sustained**: holding on to a point-of-view.
-   **Stop**: getting rid of something problematic.
-   **Start**: moving towards something beginning.
-   **Do-er**: the Main Character prefers to adapt their environment to themselves.
-   **Be-er**: the Main Character prefers to adapt themselves to their environment.
-   **Dopamine**: solving problems step-by-step through logic and cause-and-effect reasoning.
-   **Serotonin**: resolving inequities by balancing relationships and considering context.
-   **Spacetime**: an emphasis on sequencing through a re-arrangement of dramatic potentials where space is held objectively, and time is subjective.
-   **Timespace**: an emphasis on temporal sequencing where time is held objectively, and space is subjective.
-   **Action**: in terms of the objective plot, actions force decisions.
-   **Decision**: in terms of the objective plot, decisions force actions.
-   **Success**: the original goal is achieved.
-   **Failure**: the original goal is not achieved.
-   **Good**: the Main Character resolves their personal baggage.
-   **Bad**: the Main Character fails to resolve their personal baggage.
-   **Harmony**: forces align to support a stable, balanced trajectory forward.
-   **Discord**: forces disrupt balance, destabilizing the trajectory and pushing in a new direction.
-   **Higher**: the Main Character moves upward on the emotional ladder, easing personal burdens.
-   **Lower**: the Main Character moves downward on the emotional ladder, increasing personal burdens.

## 5. Dramatica Translation

NCP includes terminology that clarifies and modernizes concepts from the Dramatica theory of story. This section provides a translation map.

### Key Terminology Changes

| **Previous Term**                  | **UNM Equivalent**          | **Why the Change?**                                      |
| ---------------------------------- | --------------------------- | -------------------------------------------------------- |
| Change vs. Steadfast               | Relinquished vs. Maintained | More accurately describes the transformation process.    |
| Mental Sex/Problem-solving Style   | Narrative Alignment         | Aligns with modern neuroscience for decision-making.     |
| Story Limit                        | Narrative Fabric            | Clarifies relationship between time and space in a narrative. |
| Signposts                          | Transits                    | Frames storytelling as a dynamic interaction between objective and subjective realities. |
| Universe                           | External Framing            | Clarifies that conflict arises from external conditions shaping the context. |
| Physics                            | External Processing         | Shifts focus to dynamic action and interaction.          |
| Psychology                         | Internal Processing         | Makes it clear that conflict stems from patterns of thought and decision-making. |
| Mind                               | Internal Framing            | Highlights how attitudes and beliefs create conflict by shaping perception. |

### Terminology for Serotonin-aligned Narratives

| **Dramatica Term**    | **Serotonin-aligned Term** | **Why the Change?**                                      |
| --------------------- | -------------------------- | -------------------------------------------------------- |
| Change vs. Steadfast  | Released vs. Sustained     | More accurately describes the transformation process.    |
| Problem               | Condition                  | Reflects a more neutral framing of narrative inequities. |
| Solution              | Adjustment                 | Recognizes shifts in perspective rather than binary resolution. |
| Focus                 | Resistance                 | Highlights opposition to a problem rather than mere attention. |
| Direction             | Flow                       | Captures the evolving movement of the narrative.       |
| Story Goal            | Story Intention            | More accurately represents the driving force of the narrative. |
| Story Consequence     | Story Overwhelm            | Frames consequences as pressures influencing narrative arcs. |
| Story Dividends       | Story Excitement           | Emphasizes the payoff or anticipation within a narrative. |
| Story Costs           | Story Pressure             | Defines the weight of obstacles within a given narrative. |
| Story Forewarnings    | Story Ennui                | Reflects warning signs of stagnation or a need for change. |
| Story Requirements    | Story Habituation          | Describes conditions necessary to sustain the narrative flow. |
| Story Prerequisites   | Story Internalization      | Aligns with steps taken to integrate an evolving theme. |
| Story Preconditions   | Story Socialization        | Defines external expectations shaping the narrative.     |

## 6. Practical Example: "Anora"

The following is a condensed and formatted example from the `anora.json` file to illustrate how the Narrative Context Protocol is applied to a real story.

### Story Metadata

-   **Title**: Anora
-   **Genre**: the genre
-   **Logline**: the logline

### Subtext Example

#### Perspectives

-   **Objective Story (`they`)**: "Navigating the high-stakes world of Russian-oligarchy family dynamics."
-   **Main Character (`i` - Ani)**: "Ani is a young woman struggling to survive in a world that sees her as disposable... Her fight is grounded in the desire to be seen as more than just a commodity."
-   **Catalyst Provocateur (`you` - Igor)**: "Igor, a loyal enforcer... embodies a chilling mix of pragmatism and intimidation. He challenges Ani’s sense of agency with his cold demeanor and violent methods."
-   **Relationship Story (`we` - Protector/Protectee)**: "The bond between Ani and Igor evolves from distrust and aggression to a complicated dynamic of reluctant understanding."

#### Key Storypoints

-   **Story Intention (Objective Story)**:
    -   **Method**: `Obtaining`
    -   **Illustration**: "obtaining freedom"
    -   **Storytelling**: "The Story Intention of Obtaining manifests in Ani's relentless pursuit of agency and self-worth in a world that constantly seeks to strip her of both."

-   **Condition (Main Character)**:
    -   **Method**: `Control`
    -   **Illustration**: "someone being controlled"
    -   **Storytelling**: "Ani's MC Condition of Control is reflected in her constant struggle to assert agency over her life in a world that seeks to dominate and define her."

-   **Adjustment (Main Character)**:
    -   **Method**: `Free`
    -   **Illustration**: "abandoning"
    -   **Storytelling**: "Ani's journey revolves around her struggle with the Condition of Control... her transformative Revision to Abandon occurs when she realizes that true freedom cannot be achieved by clinging to the systems and relationships that seek to control her."

-   **Pivotal Element (Catalyst Provocateur)**:
    -   **Method**: `Control`
    -   **Illustration**: "keeping a group under control"
    -   **Summary**: "Igor illustrates that in the brutal world of the Zakharov family's criminal empire, being considerate is a strategic strength that fosters loyalty and survival, challenging Ani's views on morality and power."
