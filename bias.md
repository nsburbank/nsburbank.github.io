## Cultural Bias in AI

LLMs behave in ways that reflect the limitations of their training data. Most obviously, the languages they understand best are those most represented in the dataset used for training. Less clearly but also importantly, LLMs embody the cultural assumptions and biases of their training content. One approach that has been proposed to quantify this is mapping LLMs onto the two dimensions of the Inglehart-Welzel World Cultural Map.
<br>
![Inglehart-Welzel World Cultural Map 2023](Images/Cultural_Map_2023.png)
Source: http://www.worldvaluessurvey.org/

LLMs tend to cluster in a small area of the World Cultural Map, as shown below for OpenAI's GPT models. The same behaviour is apparent across other frontier-class models.

![GPT models overlaid on World Cultaral Map](Images/Tao_et_al.png)\
Source: https://arxiv.org/pdf/2311.14096

### Resources

[World Values Survey](https://www.worldvaluessurvey.org/)\
The organization that publishes and updates the Inglehart–Welzel Cultural Map

[Cultural Bias and Cultural Alignment of Large Language Models](https://arxiv.org/abs/2311.14096)\
Perhaps the most-cited publication examining how LLMs map onto the Inglehart-Welzel World Cultural Map. Findings limited to OpenAI models.

[The Value Atlas of AI: Mapping World Human Values in Large Language Models](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=6585679)\
A more recent paper which includes a wider set of LLMs from OpenAI, Anthropic, Google, xAI and several others.

