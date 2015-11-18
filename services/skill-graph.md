# Skill Graph

The Skill Graph is a graph of the skills, abilities, understandings, and evidence that constitute all potential learnings. They chart a grand territory of capacities and offer a map for learners to navigate by with clarity and confidence.

As a graph, there are nodes and edges. We can think of them as objects and relationships, with the understanding that objects can relate to each other in different, even asymmetrical ways.

## Use Cases

### Curriculum Integration

Any component of the curriculum (project, exercise, challenge, reading, whatever) can be tagged and associated with a particular understanding or ability. In this way the Skill Graph acts as a web binding together all of the elements of learning.

### Mindful Learning

For every moment when a learner is assigned a task or given new information, they should be able to immediately answer the questions: "why do I need to do/know this? How does this serve my greater learning? What purpose does this serve?" The Skills Graph is a system for answering these and other questions.

Mindful learning requires that learning be meaningful; for learning to be meaningful its purpose must always be clear.

### Design Consistency

As a learning/curriculum designer, I need to know how a piece of curriculum fits into the whole. I also need to know if a designed learning outcome is well supported by the requisite abilities and understandings.

### Design Transparency

When learning design is transparent to both "teachers" and "students" (or whichever roles are in play), there is no information asymmetry between the "producers" of the curriculum and the "consumers". If designed well, the Skill Graph could supplement the further dissolution of these dichotomies and foster a learning environment where learners and guides co-create the learning experience.

## Data Owned

Nodes:

- skill
  - name
- skill_level
  - skill
  - level
- ability
  - name
  - description
- understanding
  - name
  - description
- evidence
  - reflection (qualitative assessment tool)
  - metrics (quantitative assessment tool)

Edges:

- skill_level -[composes]-> skill
- skill_level -[requires]-> (skill_level / ability / understanding)
- skill_level -[benefit_from]-> (skill_level / ability / understanding)
- (ability / understanding) -[define]-> skill_level
- (ability / understanding) -[supplement]-> skill_level
- (skill_level / ability / understanding) -[proved_by]-> evidence
- evidence -[demonstrates]-> (skill_level / ability / understanding)
