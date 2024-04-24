# Project-Python

Ce code commence par présenter le profil de l'utilisateur, puis propose deux choix de stocks à investir, en demandant à l'utilisateur si son investissement peut être plus ou moins risqué, ainsi que s'il souhaite être très rentables rapidement (sur 1 an) ou rentables à long terme (sur 10 ans).
    L'utilisateur sélectionne un stock parmi Google et General Motors.
    L'utilisateur indique s'il souhaite prendre une position risquée ou non.
    L'utilisateur choisit s'il veut investir à court terme (1 an) ou à long terme (10 ans).

Ensuite, le code propose une stratégie d'investissement en fonction des choix de l'utilisateur, et retourne les résultats du backtest ainsi que des graphiques soit un schéma de signaux d'achat et de vente, ainsi que des résultats de la stratégie comme le rendement cumulatif, le ratio de Sharpe, le rendement moyen, la variance, le bêta, le bêta en hausse et en baisse, ainsi que le drawdown maximal. 

Enfin, le code demande à l'utilisateur s'il souhaite changer de stratégie.
Après avoir exécuté une stratégie et affiché les résultats, le programme demande à l'utilisateur s'il est satisfait des résultats. Si ce n'est pas le cas, l'utilisateur peut choisir de changer de stock sélectionné. Ensuite, le programme invite l'utilisateur à observer les résultats du backtest et un graphique simplifié.

Ces informations sont basées sur la source Yahoo Finance, nous avons donc pour chaque période (10 ans donc 2013-2023 et 1 an donc 2023) téléchargé les fichiers de données historiques pour chaque stock : GM, Google et VLKAF. 

Les stratégies implémentées sont les suivantes :

# Stratégie 1 : 
    Pour Google, si l'utilisateur choisit de ne pas prendre de risque et opte pour un investissement à long terme, le programme utilise l'analyse des bandes de Bollinger et l'analyse du volume pour générer des signaux d'achat et de vente.

    Explication : 
    Les Bandes de Bollinger nous aident à voir si le prix d'une action est élevé ou bas par rapport à sa plage habituelle. Lorsque le prix devient trop élevé (touchant ou dépassant la bande supérieure), cela pourrait signifier que l'action devient trop chère et qu'elle pourrait bientôt baisser. D'autre part, lorsque le prix devient trop bas (touchant ou dépassant la bande inférieure), cela pourrait signifier que l'action devient trop bon marché et qu'elle pourrait bientôt augmenter.
    Le volume confirme ces signaux Lorsque le prix d'une action change de direction et que beaucoup de personnes achètent ou vendent en même temps (indiqué par un volume accru), cela rend le signal plus fiable. C'est un peu comme si plus de personnes étaient d'accord sur quelque chose, ce qui est généralement un bon signe. 

# Stratégie 2 : 
    Pour General Motors, si l'utilisateur choisit de ne pas prendre de risque et opte pour un investissement à long terme, le programme utilise une stratégie basée sur les moyennes mobiles pour générer des signaux d'achat et de vente.
    
    Explication :
    Cela correspond à une stratégie de Momentum qui va utiliser deux moyennes mobiles exponentielles (EMA) pour déterminer les points d'entrée et de sortie du marché. En effet nous partons de ce principe : 
        IF YESTERDAY'S MA30 WAS LOWER THAN YESTERDAY'S MA100, AND TODAY'S MA30 IS HIGHER THAN TODAY'S MA100 THEN BUY
        IF YESTERDAY'S MA30 WAS HIGHER THAN YESTERDAY'S MA100, AND TODAY'S MA30 IS LOWER THAN TODAY'S MA100 THEN SELL
    
# Stratégie 3 : 
    Pour General Motors, si l'utilisateur choisit de prendre un risque, le programme compare les prix de General Motors avec un autre stock (VLKAF) pour générer des signaux d'achat et de vente en fonction de si les deux stocks sont corrélés. 

    Explication : 
    En l'occurence les deux stocks sont corrélés positivement ce qui nous permet d'en conclure des signaux suivant si les stocks s'éloignent ou se rapprochent l'un de l'autre en partant du principe qu'alors, ils se rejoindront ou divergeront et cela nous permet donc d'en déduire une prévision du mouvement du prix.

# Stratégie 4 : 
    Si l'utilisateur choisit une combinaison non couverte par les autres stratégies, le programme utilise une stratégie de trading basée sur la régression linéaire pour générer des signaux d'achat et de vente.

    Explication : 
    Nous utilisons ici une analyse de régression linéaire comme nous l'avons vu en econométrie. La régression linéaire consiste à ajuster une droite qui représente au mieux la relation linéaire entre les variables indépendantes (telles que le temps) et la variable dépendante (le prix de l'actif financier). Nous utilisons ensuite cette droite d'estimation pour en déduire les signaux d'achat et de vente. En effet, si la régression linéaire indique une tendance à la hausse, cela peut déclencher un signal d'achat, tandis qu'une tendance à la baisse peut déclencher un signal de vente.




