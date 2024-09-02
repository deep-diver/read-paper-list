# Automated Design of Agentic Systems

![1](./1.png)

✦ The research called ADAS (Automated Design of Agentic Systems) conducted at UBC proposes a framework for automatically designing agents. Conceptually, ADAS can be performed in any way, but for ease of self-evolving and evaluation, this research implements and releases a specific framework called Meta Agent Search, which discovers new agents based on "code". According to this paper, the term Agent is not clearly defined, and in this paper, an Agent is considered a kind of Agentic System that uses a Foundation Model to "plan", "use tools", "derive results", and "iterate" to solve specific problems.

✦ ADAS is proposed as a new research field based on a strong belief in the trend that "algorithms directly designed by humans will eventually be replaced by AI's automated structure discovery". This is inspired by the research trend where image recognition techniques that used to rely on manually written patterns were replaced by CNNs, and the structural patterns of such CNNs or neural networks are being replaced by AutoML/NAS. (To be precise, they haven't been completely replaced, and there are various cost aspects to consider, but the models with the best performance reported in academia have been discovered by these automated techniques).

✦ Therefore, the abstract operation of ADAS is similar to existing AutoML:
- Define the Search Space
- Define the Search Algorithm to find the optimal agent in the Search Space
- Define the Evaluation Algorithm to evaluate the found agent
- Repeat this process to find the optimal agent
- The agents discovered in this process are archived and used to discover the next optimal agent

![2](./2.png)

✦ To demonstrate ADAS, Meta Agent Search (MAS) was implemented. MAS follows the ADAS process as is, but is limited to solving problems through "coding". There are various reasons, but it seems that interpretation and actual evaluation are easier because the output is "code". In the specific implementation, GPT-4o was used as the Meta Agent, GPT-3.5-Turbo was used for evaluating the results, and [COT, COT_SC, Reflexion, LLM_debate, Take_a_step_back, QD, Role_Assignment] were placed as basic FM modules in the Search Space, then the Search Algorithm was repeated 25-50 times.

![3](./3.png)

✦ MAS was experimented on a total of 4 benchmarks: ARC, [Reading Comprehension(DROP), Math(MGSM), Multi-Task(MMLU), Science(GSM8K)], and showed significantly higher performance than agents applying each of the manually designed techniques COT, COT_SC, Reflexion, LLM_debate, Take_a_step_back, QD, Role_Assignment. Additionally, by switching the Foundation models of the top 3 optimal Agents discovered through GPT4o to Claude Haiku, GPT4, and Claude 3.5 Sonnet and still maintaining a high level of performance, it was confirmed that the discovered Agents have "transferability/generalizability".

✦ Personal impressions:
- Methods like AutoML/NAS find the optimal model, but they incur very high costs. However, techniques like ADAS simply(?) call Foundation Models, and because prices are rapidly decreasing, it feels less burdensome. The report states that it costs about $500 to discover one optimal agent, but personally, I think it might not cost that much if various optimization points are improved.

- Despite being a very simple idea, the code is implemented quite messily. It would have been good to create a kind of framework, but it's a bit disappointing that it's hardcoded to perform Search for specific benchmarks. I think someone who's good at coding will soon turn it into a framework and release it.

- There are also some limitations. Defining the initial Search Space is very important, and what's specified in this paper includes Agents designed manually by humans in the Space set. No matter how much "automation" becomes a future trend, I think Agents manually designed to derive "optimal results" in "short steps" will continue to be proposed. The more this happens, the more naturally ADAS will be able to take advantage of their benefits. However, I think there are difficulties in determining whether the optimal Agent is truly "optimal". But I think it might be possible for humans to look at what's discovered as "optimal" and further "compress" the process to optimize it more.

- Basically, this can be seen as one of the studies opening up the horizon of the new(?) research field called ADAS, and thanks to(?) this, I think various studies based on this can flourish (depending on the perspective, it seems to share some similarities with things like DSPy).

Link: https://arxiv.org/abs/2408.08435