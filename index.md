# X Zhang's PS 811 GitHub Portfolio Pages


# Research interest
- the psychological sources of conflict
- the domestic sources of international conflict

# Data
- Simulation of conjoint experiment data
- Twitter Data
- Weibo Data: https://hub.hku.hk/cris/dataset/dataset107483
- LobbyView 

# A Potential question
- How regime types affect the legislative consequences of foreign lobbies in the US congress.
- Are conflict-seeking individual more likely to be attentive members of the public?

# Method
- Experiments
- Quasi-experiments
- Machine Learning

# Some visualization for the ongoing project

![top features](https://github.com/14XZ/Audience-Reward/blob/master/top%20keywords.png)


```markdown
relevant_ex_17 <- week17 %>%
  filter(str_detect(text, "黄岩岛"))

w17_hy_corpus <- corpus(relevant_ex_17$text)

# tokenize
w17_hy_toks <- w17_hy_corpus %>% 
    tokens(remove_punct = TRUE) %>%
    tokens_remove(pattern = ch_stop)

# construct a dfm
w17_hy_dfm <- dfm(w17_hy_toks)

#counting word frequency
w17_hy_topfeatures <- topfeatures(w17_hy_dfm, 50)
w17_hy_topfeatures <- data.frame(w17_hy_topfeatures)
w17_hy_topfeatures["Words"] <- rownames(w17_hy_topfeatures)

ggplot(w17_hy_topfeatures, aes(x=reorder(Words, -w17_hy_topfeatures), y=w17_hy_topfeatures))+
  geom_bar(stat = "identity", fill="orangered3")+
  theme(axis.text.x = element_text(angle = 90, hjust = 1)) + xlab("Feature") + ylab("Count") +
  labs(title = "top keywords in post mentioning Scarborough Shoal", caption = "Other than reference to the location and two conflicting states, top keywords include terms such as 'sovereignty' and 'oil'", x = "year", y = "team runs per game" )
```  
![wordcloud](https://github.com/14XZ/Audience-Reward/blob/master/top%20keywords%20word%20cloud.png)

```markdown
# plot a word cloud
set.seed(811)

# wordcloud
textplot_wordcloud(w17_hy_dfm, min_count = 15, random_order = FALSE,
                   rotation = .25, max_words = 100,
                   min_size = 1, max_size = 5,
                   font = if (Sys.info()['sysname'] == "Darwin") "SimHei" else NULL,
                   color = RColorBrewer::brewer.pal(8, "Dark2"))
                   
```




