# CSPB_3202_Final_Project
# Overview
This project uses the Stable Baselines3 library to look at two different RL algorithms and how they learn and interact in the Lunar Lander v3 environment from OpenAI's gymnasium. 
# PPO
The Proximal Policy Optimization (PPO) algorithm is a policy gradient method, which is slightly different from the algorithms we have looked at in this class. PPO is the [default algorithm used at OpenAI](https://openai.com/index/openai-baselines-ppo/) and has a few characteristics that make it ideal for there uses. Since it is a gradient policy, PPO looks to take relatively small steps in learning, makeing deviation from the previous iteration smaller than other algorithms.

Per the page linked above, the algorithm OpenAI uses is:

$L^{CLIP}(\theta)=\hat{E}_tmin(r_t(\theta))\hat{A}_t,clip(r_t(\theta),1-\varepsilon,1+\varepsilon)\hat{A}_t$

With the following descriptions:

<li>
  <ul>$\theta$ is the policy parameter</ul>
  <ul>$\hat{E}_t$ denotes the empirical expectation over timesteps</ul>
  <ul>$r_t$ is the ratio of the probability under the new and old policies, respectively</ul>
  <ul>$\hat{A}_t$ is the estimated advantage at time $t$</ul>
  <ul>$\varepsilon$ is a hyperparameter, usually 0.1 or 0.2</ul>
</li>

$\hat{A}_r$ is one of the essential pieces of the PPO algorithm since it helps decide if an action is better worse in a specific state. $A = Q - V$ is used to find the value of $A$. $Q$ is the discounted sum of rewards for completing an episode and $V$ is the baseline estimate that is the expected outcome starting from the current point. If $A>0$, then the action is better than expected.

The ratio function ($r_t$) looks at whether the agent is more likely to choose in action in the old policy or new policy and is used to estimate how the policy changes from iteration to iteration.

The hyperparameters noted above are the "clipping" that takes place in order to maintain a conservative outlook when learning. This means the amount of credit, either good or bad, that a certain action can get is contained within bounds. The agent then has two probability ratios, a clipped and unclipped, and whichever is the minimum is the lower bound for the objective, meaning it is the safest move possible.

# DQN

The Deep Q Network (DQN) implemented by Stable Baselines3 is very similar to the algorithm we looked at this semester. It examines the environment, takes a list of actions, and determine a future discounted reward to assess what action to take.

# Results/Conclusions

First, we will look at the performance of DQN. As we can see 
![DQN chart](/media/DQN_perf_chart.png "DQN Performance Chart") 


![PPO chart](/media/PPO_perf_chart.png "PPO Performance Chart")
