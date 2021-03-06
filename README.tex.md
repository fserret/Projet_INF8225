# Projet INF8225

## Description  
Initialement, le projet consistait à observer les effets de la combinaison de l’une des méthodes de curiosité ci-dessous:  
**Curiosity-driven Exploration by Self-supervised Prediction**  
https://arxiv.org/abs/1705.05363  
**Exploration by Random Network Distillation**  
https://arxiv.org/abs/1810.12894  
Ou encore la méthode utilisée pour les Agents de Never Give Up et Agent 57 si le temps le permet (peu probable)  
**NGU**: https://arxiv.org/abs/2002.06038  
**Agent 57**: https://arxiv.org/abs/2003.13350  


Avec la méthode de Imitation reinforcement learning suivante:  
**SQIL: Imitation Learning via Reinforcement Learning with Sparse Rewards**  
https://arxiv.org/abs/1905.11108  
Cette méthode d’imitation reinforcement learning permet, d’après https://arxiv.org/abs/2004.00993, quand on l’utilise comme training initial d’accélérer la convergence pour du reward-based RL traditionnelle, tout comme les méthodes de curiosité.
Nous souhaitions voir si la combinaison de cette méthode avec de la curiosité, et/ou un entraînement initial séquentiel Imitation puis curiosité(ou vice-versa) permettrait d’améliorer les performances d’un modèle de RL au-delà des deux méthodes séparé. L'idée étant d'avoir une sorte de curiosité 'guidée' par l'imitation.  


Contrairement a ce qui été prévu et dû a un manque de temps pour l'implémentation de la méthode SQIL(car repository github utilisable introuvable),  nous avons décidé de définir un reward intrinsèque guidée par les demonstrations d'un agent expert. Pour ce faire nous avons utilisée une méthode similaire au pseudo-count de la mémoire épisodique de l'agent NGU mais pour comparée les observations de notre agent avec celles des démonstrations de notre agent expert.
Par manque de temps, et comme nous nous intéressons ici à ce que les états soit similaire nous avons utilisée directement les produit scalaire entre les vecteurs de features crées par le random target network du modèle en cours d'entrainement comme kernel de similarité, ensuite nous combinons le reward ainsi obtenu avec le reward de curiosité comme suit:

\begin{equation}
r_{im} = \frac{\sum_{v\in \text{Demonstrations}} X_{obs}\cdot v}{|\text{Demonstrations}|}
\end{equation}

\begin{equation}
r_{int} = r_{rnd} \cdot (1 + tanh(\alpha \cdot r_{im}))
\end{equation}

Le code utilisé/developpé dans ce repository est basé sur le repository github suivant:  
**Exploration by Random Network Distillation**  
https://github.com/openai/random-network-distillation


# Testing code
run_imitation_agent_colab.ipynb can be used to create a suitable python environment and run the imitation agent.
Note: Due to the limited duration of colab instance, all the training reported was done locally using a GTX 1070, 16gb of RAM and a core i7 on Ubuntu 18.04, the notebook is only for code testing and not actual training of the agent
