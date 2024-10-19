---
title: Markov Decision Processes 
date: 2021-06-01 23:54:22
mathjax: true
tags:
- Machine-Learning
- Markov-Decision-Process
- Reinforcement-Learning
categories:
- Reinforcement-Learning
ShowToc: true
---
# Markov Property (MP)
<!--more-->
## Markov Property (MP)

- **The probability of reaching S’ from S only depends on S, not on the history of earlier states**
- Fundamental of Bellman Equations (mentioned later)

## Markov Decision Processes (MDPs)

- 
  
    ![](https://datawhalechina.github.io/easy-rl/chapter2/img/2.2.png)
    
    
    
- The mathematical description of reinforcement learning is based on Markov Decision Process, which can be described as tiple: **(S, A, R, P, ρ0)**
  
    where **S**：set of all possible states
    
     **A**: set of all possible actions
    
     **R**: rewards function
    
     **P**: state transition function: P(s’ | s, a ) probability of s’ if take action a in state s
    
     **ρ0**：The initial state distribution
    

## Discounted Return

### Trajectory

- trajectory *τ* is the set of states and actions

*τ* = (*s*0, *a*0, *s*1, *a*1,  ·  ·  · )

### Reward and Return

- The reward is the encouragement of a single step while the return is the cumulative rewards on a whole trajectory
- Usually, we will consider the discounted factor on the return, hence:

$$
R(\tau) = \sum_{t=0}^{\infty}\gamma^t r_t
$$

- Why do we need discounted factor ?
  
    **Cash now is better than cash later**
    

## Value Function

- State Value function *Vπ*(*s*)​ To estimate **how good** it is for the agent to be in a **given state** under policy *π*​​ *Vπ*(*s*) = *Eτ* ∼ *π*[*R*(*τ*) | *s*0 = *s*]
- Action Value function *Qπ*(*s*, *a*)
  
    To estimate **how good** it is for the agent to be in a **given state and action** under policy *π* *Qπ*(*s*, *a*) = *Eτ* ∼ *π*[*R*(*τ*) | *s*0 = *s*, *a*0 = *a*]
    

## Bellman Equation

- It is frequent to estimate the value function in reinforcement learning. Bellman equation is the method to implement. The basic idea behind Bellman Equation is : **Current Value = Current Reward + Future Value**

### Recursive Relation in Reinforcement Learning

- A fundamental property of value functions used throughout reinforcement learning is that it satisfy particular recursive relationship. The **Backup Operation** transfer value information back to a state/state-action pair from its successor states/state-action pairs.

### Backup Diagram

![](https://datawhalechina.github.io/easy-rl/chapter2/img/state_value_function_backup.png)



- As the above diagram illustrated, the calculation of state-value function can be decomposed into two steps:
  
    Before derivation: black dots stand for state, action pairs, white dots stands for action. Lines in B stands for policy probability, lines in C stands for states transition probability.
    
    In diagram B:
    

*Vπ*(*s*) = ∑*a* ∈ *Aπ*(*a*|*s*)*Qπ*(*s*, *a*)

 In diagram A: *Qπ*(*s*, *a*) = *R*(*s*, *a*) + *γ*∑*s*′ ∈ *SP*(*s*′|*s*, *a*)*vπ*(*s*′) ​ Merging equation A and B, we get one form of **Bellman Equation for *Vπ*** *Vπ*(*s*) = ∑*a* ∈ *Aπ*(*s*|*a*)(*R*(*s*, *a*) + *γ*∑*s*′ ∈ *SP*(*s*′|*s*, *a*)*vπ*(*s*′))

## Summary

- **Bellman Equation(s) defines a connection between the current state and future state**

- Given the simplified form of Bellman Equations
  
  
$$
\begin{cases}V^\pi(s)=\mathbb{E}[r(s,a)+\gamma V^\pi(s')]\\Q^\pi(s,a)=\mathbb{E}[r(s,a)+\gamma \mathbb{E}[Q^\pi(s',a')]]\\V^*(s)=\max_{a}\mathbb{E}[r(s,a)+\gamma V^*(s')]\\Q^*(s,a)=\mathbb{E}[r(s,a)+\gamma \max_{a'}Q^*(s',a')]\end{cases}
$$

