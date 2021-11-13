# AI-Advanced-Search-Algorithms

Implementation of Artificial Intelligence advanced search algorithms

## Hill climbing
Very simple idea: Start from some state s,
Move to a neighbor t with better score. Repeat.

#### Question: What’s a neighbor? 
• (vaguely) Problems tend to have structures. A small change produces a neighboring state.
• The neighborhood must be small enough for efficiency
• Designing the neighborhood is critical. This is the real ingenuity – not the decision to use hill climbing.

#### Question: Pick which neighbor?
The best one (greedy)

#### Question: What if no neighbor is better than the current state?
Stop. (Doh!)

### Hill climbing algorithm
1. Pick initial state s
2. Pick t in neighbors(s) with the largest f(t)
3. IF f(t) <= f(s) THEN stop, return s
4. s = t. GOTO 2.

## Simulated annealing

### Simulated annealing algorithm
1. Pick initial state s
2. Randomly pick t in neighbors(s) 
3. IF f(t) better THEN accept st. 
4. ELSE /* t is worse than s */
5. accept st with a small probability
6. GOTO 2 until bored.

current = Initial-State(problem)
for t = 1 to infinit do<br>
  - T = Schedule(t) ; // T is the current temperature, which is monotonically decreasing with t<br>
  - if T=0 then return current ; //halt when temperature = 0<br>
  - next = Select-Random-Successor-State(current)  <br>
  - deltaE = f(next) - f(current) ; // If positive, next is better than current. Otherwise, next is worse than current. <br>
  - if deltaE > 0 then current = next; // always move to a better state<br>
  - else current = next with probability p = exp(deltaE / T); // as T -> 0, p -> 0; as deltaE -> -infinit , p -> 0 <br>
end

### Simulated Annealing issues

• Cooling scheme important <br>
• Neighborhood design is the real ingenuity, not the decision to use simulated annealing. <br>
• Not much to say theoretically <br>
  • With infinitely slow cooling rate, finds global optimum with probability 1. <br>
• Proposed by Metropolis in 1953 based on the analogy that alloys manage to find a near global minimum energy state, when annealed slowly. <br>
• Easy to implement. <br>
• Try hill-climbing with random restarts first! <br>
