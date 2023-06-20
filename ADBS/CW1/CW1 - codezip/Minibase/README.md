**Task2**
	(It is much more detailed here. The logic is also explained in the QueryInterpreter class. and each step is explained with in-line comment)
	
1. Iterate through the relationatoms. 
	1. If some variables has occurred before, substitute with a new variable so that each variable occurs exactly once. Add a join condition for the sub with the original one. For example, R(x, y), S(x, z) => R(x, y), S(xSub, z), x = xSub
	2.  Create a scanOperator for each relational atom (with variable substituted), store it in a map with the relation name as the key. 
	3.  Record the relation of each variable where it is contained in a map (varMap). 

2. Iterate through the comparisonAtoms. 
	1.  Check if it is a selection or join (count the number of relations involved by referring to varMap)
	2.  If it is a selection condition (involves only one relation), add it to the list of comparison atom corresponding relation. For example, all selecions on R will be added into the list of conditions, stored in a map with "R" as its key (joinConditions). Then selection conditions will be added into body for all its terms' substitutions. For example, R(x), S(x), x < 5 => R(x), S(xSub), x < 5, xSub < 5
	3.  If it is a join condition (involves two relations),  add it to a list of join conditions for further pick. 

3. Iterate through the joinConditions map. 
   1. Each key of the map represents a relation whose tuples are selected, so we create a select operator, with scan operator of that relation as its child and the list of Comparisonatom as the conditions. 
   2. Each select operator is storeed in a map with the relation name as its key. 

4. Iterate through the relations to perform left-deep join
   1. Start with the first relation. If is has a select operator, we set it as the root, otherwise use its scan operator as the root. 
   2. For each further relation, we create a join operator, with the previous root as the left child. And if it has a select operator, set it as the right child, otherwise use its scan operator. 
   3. Having set the two children, we collect conditions involving these two relations as the join conditions

5. Aggregate and projection
   1. We create a sumOperator or projection operator with the root before as its child to produce the final result. 

**All logic of operators are explained in corresponding classes**