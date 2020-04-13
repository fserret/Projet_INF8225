# Projet_INF8225

Projet INF8225

Description
Le projet consisterait à observer les effets de la combinaison de l’une des méthodes de curiosité ci-dessous:
Curiosity-driven Exploration by Self-supervised Prediction
https://arxiv.org/abs/1705.05363
Exploration by Random Network Distillation
https://arxiv.org/abs/1810.12894
Ou encore la méthode utilisée pour les Agents de Never Give Up et Agent 57 si le temps le permet (peu probable)


NGU: https://arxiv.org/abs/2002.06038
Agent 57: https://arxiv.org/abs/2003.13350


Avec la méthode de Imitation reinforcement learning suivante:
SQIL: Imitation Learning via Reinforcement Learning with Sparse Rewards
https://arxiv.org/abs/1905.11108
Cette méthode d’imitation reinforcement learning permet, d’après https://arxiv.org/abs/2004.00993, quand on l’utilise comme training initial d’accélérer la convergence pour du reward-based RL traditionnelle, tout comme les méthodes de curiosité.
Nous souhaitons donc voir si la combinaison de cette méthode avec de la curiosité, et/ou un entraînement initial séquentiel Imitation puis curiosité(ou vice-versa) permettrait d’améliorer les performances d’un modèle de RL au-delà des deux méthodes séparé. L'idée étant d'avoir une sorte de curiosité 'guidée' par l'imitation.

Liens Code Github
Curiosity-driven Exploration by Self-supervised Prediction
https://github.com/pathak22/noreward-rl
SQIL: Imitation Learning via Reinforcement Learning with Sparse Rewards
https://github.com/dnishio/DSAC
Code Projet
https://github.com/fserret/Projet_INF8225
