​	

# Natural Language Processing & Word Embeddings



1. voca에 6만단어가 있을 때, embedding vectors의 차원은 voca보다 작다. 보통 50~1000차원을 사용한다.

2. t-SNE는 비선형차원축소 방법이다.

3. 큰 사이즈의 corpus에서 훈련된 pre-trained word embedding 을 활용한 예시이다.

   1.  문장의 기분을 분류하는 RNN모델을 구축할 때 활용할 수 있는 예시

      + 아래와 같은 training set이 있을 때, `I feel wonderful!` 을 1로 분류할 수 있게 된다. (awesome과 wonderful이 가깝기 때문)

      ![image-20230919211431785](Quiz.assets/image-20230919211431785.png)

4. 좋은 word embedding을 위해서 유지되어야 할 방정식은?
   + $e_{man} - e_{king} \simeq e_{woman}-e_{queen}$
   + $e_{man} - e_{woman} \simeq e_{king}-e_{queen}$



5. $A$가 embedding matrix이고, $o_{4567}$이 one-hot vector라고 하자. Embedding of word 4567인 $e_{4567}$을 구하려고 할 때, $A*o_{4567}$을 하여 구하지 않는 이유는?
   + 계산이 비효율적이기 때문이다. 그냥 $A$의 index를 호출하면 $O(1)$의 속도로 계산가능하다.
     + $A$의 차원은 $\text{vocabsize} \times \text{사용자정의임베딩차원}$ 이다.

6. Word embedding을 훈련시킬 때, $P(\text{target}|\text{context})$ 를 활용했다. 이 때 예측 성능은 좋지 않아도, word embedding을 잘하는 것이 중요하다.



7. Word2vec 알고리즘에서 $P(t|c)$를 추정하는데, $t,c$를 trianing set에서 어떻게 고르는가?
   + 앞 뒤 구분없이 nearby words로 고른다.



8. 1만개의 voca가 있고, 500 dim의 word embedding을 훈련시키는 상황에서, 아래와 같은 softmax function을 사용하는 word2vec model을 생각하자. 

$$
P(t \mid c)=\frac{e^{\theta_t^T e_c}}{\sum_{t^`=1}^{10000} e^{\theta_{t^`}^T e_c}}
$$

+ 이 때 $\theta_t$ and $ e_c$는 모두 최적화 알고리즘에 의해 훈련되고, 최적화 알고리즘은 Adam이나 Gradient descent 등을 사용함
+ 이 때 $\theta_t$ and $ e_c$는 모두 500 차원 vector이다. 



10. 데이터 set $s_1$에서 훈련된 word embedding을 가지고 있고, 데이터 set $s_2$에서 language task를 수행하려고 한다. 이 때에 데이터 set크기는 어때야할까?
    + $s_1 >> s_2$ 인 경우에 이미 훈련된 word embedding을 쓰는 것이 효과적이다.