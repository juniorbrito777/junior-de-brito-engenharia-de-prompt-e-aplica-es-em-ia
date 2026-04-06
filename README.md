# 🚀 Engenharia de Prompt e Aplicações em IA

Uma guia completa sobre engenharia de prompt, técnicas avançadas e aplicações práticas em Inteligência Artificial.

## 📋 Índice

- [O que é Engenharia de Prompt?](#o-que-é-engenharia-de-prompt)
- [Conceitos Fundamentais](#conceitos-fundamentais)
- [Técnicas de Engenharia de Prompt](#técnicas-de-engenharia-de-prompt)
- [Aplicações Práticas](#aplicações-práticas)
- [Boas Práticas](#boas-práticas)
- [Exemplos de Código](#exemplos-de-código)
- [Recursos e Referências](#recursos-e-referências)

## 🤖 O que é Engenharia de Prompt?

Engenharia de Prompt é a disciplina de projetar e otimizar instruções (prompts) para extrair o máximo de desempenho e qualidade dos modelos de linguagem de IA. É uma habilidade crucial na era dos modelos generativos como GPT-4, Claude, Gemini e outros.

### Por que é Importante?

- **Melhor Qualidade de Resultados**: Prompts bem estruturados geram respostas mais precisas e relevantes
- **Eficiência**: Reduz iterações necessárias para obter o resultado desejado
- **Economia de Tokens**: Minimiza o uso desnecessário de recursos computacionais
- **Consistência**: Garante resultados reproduzíveis e confiáveis

## 📚 Conceitos Fundamentais

### 1. **Componentes de um Prompt Efetivo**

```
[CONTEXTO] → [INSTRUÇÃO] → [FORMATO] → [EXEMPLO]
```

| Componente | Descrição | Exemplo |
|-----------|-----------|---------|
| **Contexto** | Situação ou background | "Você é um especialista em dados" |
| **Instrução** | O que fazer | "Analise este dataset" |
| **Formato** | Como estruturar a resposta | "Retorne em JSON" |
| **Exemplo** | Output esperado (few-shot) | Mostrar formato desejado |

### 2. **Tokens e Custo Computacional**

- Um token ≈ 4 caracteres
- Influencia custo e velocidade de resposta
- Otimização de prompts reduz consumo

### 3. **Temperatura e Parâmetros**

```python
temperature = 0.0    # Respostas determinísticas
temperature = 0.7    # Equilíbrio criatividade/consistência
temperature = 1.0+   # Respostas criativas e aleatórias
```

## 🎯 Técnicas de Engenharia de Prompt

### 1. **Zero-Shot Prompting**

Fazer uma tarefa sem exemplos prévios.

```
Prompt: "Classifique o sentimento: 'Adorei este produto!'"
Resposta: "Positivo"
```

### 2. **Few-Shot Prompting**

Fornecer um ou mais exemplos antes da tarefa real.

```
Exemplos:
- "Ótimo produto!" → Positivo
- "Péssima qualidade" → Negativo

Classifique: "Produto OK, nada demais"
Resposta: "Neutro"
```

### 3. **Chain-of-Thought (CoT)**

Incentivar o modelo a "pensar em voz alta".

```
Prompt: "Pense passo a passo: Se eu tenho 5 maçãs 
e ganhei 3 mais, quantas tenho?"

Resposta: "Etapa 1: Comecei com 5 maçãs
Etapa 2: Ganhei 3 maçãs
Etapa 3: 5 + 3 = 8
Resposta: 8 maçãs"
```

### 4. **Self-Consistency**

Gerar múltiplas respostas e usar a mais comum.

```
Executar CoT múltiplas vezes → Votar na resposta mais frequente
Melhora precisão em tarefas de raciocínio
```

### 5. **Role-Playing / Persona**

Definir um papel específico para o modelo.

```
"Você é um especialista em segurança cibernética 
com 20 anos de experiência. Explique..."
```

### 6. **Prompt Estruturado com Sections**

```
### CONTEXTO
Você é um crítico de filmes experiente.

### TAREFA
Analise o seguinte filme e forneça uma avaliação.

### FORMATO
- Nota: X/10
- Pontos Fortes: [lista]
- Pontos Fracos: [lista]
- Recomendação: Sim/Não

### FILME
[descrição do filme]
```

### 7. **Temperature e Criatividade Controlada**

```
Tarefas analíticas: temperature = 0.0-0.3
Escrita criativa: temperature = 0.7-0.9
Brainstorm: temperature = 1.0+
```

### 8. **Prompt Negative (Anti-Prompt)**

Especificar o que NÃO fazer.

```
"Gere um resumo da lei, sem linguagem jurídica complexa,
sem siglas não explicadas, e evite detalhes desnecessários."
```

## 💼 Aplicações Práticas

### 1. **Análise de Dados e Insights**

```python
prompt = """
Analise estes dados de vendas e identifique:
1. Tendências principais
2. Anomalias
3. Recomendações de ação

Dados: [CSV ou dados estruturados]

Formato: Retorne em JSON com as seções acima.
"""
```

### 2. **Geração de Conteúdo**

- Blog posts e artigos
- Copywriting e marketing
- Social media content
- Documentação técnica

### 3. **Tradução e Localização**

```python
prompt = """
Traduza mantendo contexto cultural e tom:
- Idioma de entrada: Português
- Idioma de saída: Inglês
- Contexto: E-commerce
- Tom: Profissional mas amigável

Texto: [seu texto aqui]
"""
```

### 4. **Programação e Debugging**

```python
prompt = """
Função: Validar CPF em Python
Requisitos:
- Verificar formato correto
- Validar dígitos verificadores
- Retornar True/False
- Inclua testes

Linguagem: Python 3.9+
"""
```

### 5. **Suporte ao Cliente (Chatbots)**

```python
system_prompt = """
Você é um assistente de suporte amigável.
- Responda em português (PT-BR)
- Seja conciso mas útil
- Se não souber, redirecione para especialista
- Mantenha tom profissional e empático
"""
```

### 6. **Pesquisa e Educação**

```python
prompt = """
Explique Blockchain para:
1. Uma criança de 8 anos
2. Um estudante de engenharia
3. Um CEO de empresa

Formato: Três explicações separadas, do mais simples 
para o mais técnico.
"""
```

### 7. **SEO e Palavras-Chave**

```python
prompt = """
Para o tema "Machine Learning em Saúde":
- Gere 10 palavras-chave de alta relevância
- Crie 5 títulos otimizados para SEO
- Forneça meta descriptions (160 caracteres)

Formato: Lista estruturada em Markdown
"""
```

## ✅ Boas Práticas

### 1. **Seja Específico**

❌ Ruim: "Escreva sobre IA"
✅ Bom: "Escreva um artigo de 500 palavras sobre aplicações de IA em medicina diagnóstica"

### 2. **Forneça Contexto Claro**

```python
# ❌ Ruim
"Analise estes dados"

# ✅ Bom
"Você é um analista de dados com experiência em e-commerce.
Analise estes dados de vendas Q1 2024 para identificar 
padrões de compra por região."
```

### 3. **Use Delimitadores**

```
"""
[Seu texto aqui]
"""

---

[Seção separada]
```

### 4. **Especifique o Formato de Saída**

```python
prompt = """
...seu prompt...

Retorne EXATAMENTE neste formato JSON:
{
  "resultado": "valor",
  "confiança": 0.0-1.0,
  "detalhes": "explicação"
}
"""
```

### 5. **Itere e Refine**

1. Crie um prompt inicial
2. Teste e avalie resultados
3. Identifique deficiências
4. Refine e otimize
5. Repita

### 6. **Use Exemplos (Few-Shot)**

Forneça 1-3 exemplos de formato esperado antes da tarefa real.

### 7. **Divida Tarefas Complexas**

```
Tarefa Grande → Múltiplas Subtarefas → Agregar Resultados
```

### 8. **Monitore Custos de Token**

Ferramentas como `tiktoken` ajudam a contar tokens:

```python
import tiktoken

encoding = tiktoken.encoding_for_model("gpt-4")
tokens = encoding.encode("seu prompt aqui")
print(len(tokens))  # Número de tokens
```

## 💻 Exemplos de Código

### Exemplo 1: Análise de Sentimento

```python
import openai

def analyze_sentiment(text, language="pt-BR"):
    prompt = f"""
    Analise o sentimento do seguinte texto em {language}:
    
    Texto: "{text}"
    
    Retorne em JSON:
    {{
        "sentimento": "positivo/negativo/neutro",
        "confiança": 0.0-1.0,
        "justificativa": "explicação breve"
    }}
    """
    
    response = openai.ChatCompletion.create(
        model="gpt-4",
        messages=[{"role": "user", "content": prompt}],
        temperature=0.3
    )
    
    return response.choices[0].message.content

# Uso
resultado = analyze_sentiment("Adorei este produto!")
print(resultado)
```

### Exemplo 2: Geração de Conteúdo com Chain-of-Thought

```python
def generate_blog_post(topic, audience, length="1000"):
    prompt = f"""
    Você é um especialista em marketing e copywriting.
    
    TAREFA: Crie um blog post
    TÓPICO: {topic}
    PÚBLICO-ALVO: {audience}
    COMPRIMENTO: {length} palavras
    
    INSTRUÇÕES:
    1. Comece com um gancho interessante
    2. Desenvolva a ideia em 3-4 seções
    3. Inclua exemplos práticos
    4. Finalize com call-to-action
    5. Use linguagem acessível
    
    Pense passo a passo antes de escrever.
    """
    
    response = openai.ChatCompletion.create(
        model="gpt-4",
        messages=[{"role": "user", "content": prompt}],
        temperature=0.7,
        max_tokens=1500
    )
    
    return response.choices[0].message.content

# Uso
post = generate_blog_post(
    topic="Inteligência Artificial no Trabalho",
    audience="Profissionais de TI",
    length="1200"
)
print(post)
```

### Exemplo 3: Few-Shot Learning

```python
def classify_email(email_text):
    prompt = """
    Classifique os seguintes emails como SPAM ou LEGÍTIMO.
    
    EXEMPLOS:
    Email: "Parabéns! Você ganhou R$ 1.000.000!"
    Classificação: SPAM
    
    Email: "Olá João, aqui está o relatório que você solicitou."
    Classificação: LEGÍTIMO
    
    Email: "Clique aqui e ganhe prêmios incríveis agora!"
    Classificação: SPAM
    
    CLASSIFIQUE:
    Email: "{email_text}"
    Classificação: 
    """
    
    response = openai.ChatCompletion.create(
        model="gpt-4",
        messages=[{"role": "user", "content": prompt}],
        temperature=0.0  # Determinístico
    )
    
    return response.choices[0].message.content.strip()

# Uso
resultado = classify_email("Promoção especial: 50% de desconto hoje!")
print(resultado)
```

### Exemplo 4: Prompt com Sistema (System Prompt)

```python
def chat_with_expert(user_message, expertise="Ciência de Dados"):
    system_prompt = f"""
    Você é um especialista em {expertise} com 15 anos de experiência.
    - Respostas técnicas mas compreensíveis
    - Cite exemplos práticos quando possível
    - Corrija conceitos errados educadamente
    - Sugira recursos para aprendizado adicional
    - Linguagem: Português Brasileiro
    """
    
    response = openai.ChatCompletion.create(
        model="gpt-4",
        messages=[
            {"role": "system", "content": system_prompt},
            {"role": "user", "content": user_message}
        ],
        temperature=0.5
    )
    
    return response.choices[0].message.content

# Uso
resposta = chat_with_expert(
    "Como começar com Machine Learning?",
    expertise="Machine Learning"
)
print(resposta)
```

## 🔍 Técnicas Avançadas

### 1. **Prompt Chaining**

Quebrar problemas em etapas sequenciais:

```
Prompt 1: Extrair informações
    ↓
Prompt 2: Processar dados extraídos
    ↓
Prompt 3: Gerar insights
    ↓
Resultado Final
```

### 2. **Tree of Thoughts**

Explorar múltiplas linhas de raciocínio:

```
Problema
├── Caminho 1 → Solução A
├── Caminho 2 → Solução B
└── Caminho 3 → Solução C

Melhor solução = Comparar e selecionar
```

### 3. **Prompt Refinement com Feedback**

```
Versão 1 → Teste → Feedback → Versão 2 → Teste → ...
```

## 🛠️ Ferramentas Úteis

| Ferramenta | Descrição | Link |
|-----------|-----------|------|
| **OpenAI Playground** | Testar prompts interativamente | https://platform.openai.com/playground |
| **Prompt Engineering Guide** | Guia completo | https://www.promptingguide.ai |
| **LangChain** | Framework para aplicações com LLMs | https://langchain.com |
| **tiktoken** | Contar tokens Python | https://github.com/openai/tiktoken |
| **PromptBase** | Marketplace de prompts | https://promptbase.com |

## 📚 Recursos e Referências

### Estudos Importantes

- [Chain-of-Thought Prompting Elicits Reasoning in Large Language Models](https://arxiv.org/abs/2201.11903)
- [Self-Consistency Improves Chain of Thought Reasoning in Language Models](https://arxiv.org/abs/2203.11171)
- [The Prompt Report: A Systematic Survey of Prompt Engineering](https://arxiv.org/abs/2307.06032)

### Comunidades

- [OpenAI Community Forums](https://community.openai.com)
- [HuggingFace Discussions](https://huggingface.co/discussions)
- [r/PromptEngineering](https://reddit.com/r/PromptEngineering)

### Cursos e Tutoriais

- DeepLearning.AI - Prompt Engineering
- Coursera - Generative AI
- YouTube - Content creators: Jeremy Howard, Andrej Karpathy

## 🎓 Conclusão

Engenharia de Prompt é uma habilidade essencial na era da IA. Com as técnicas e práticas descritas neste guia, você está preparado para:

✅ Criar prompts efetivos e bem estruturados
✅ Otimizar respostas de modelos de IA
✅ Economizar tokens e recursos computacionais
✅ Aplicar IA em problemas reais e complexos
✅ Colaborar melhor com modelos generativos

**Lembre-se**: A melhor engenharia de prompt vem da prática contínua e experimentação!

---

## 📝 Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

## 👤 Autor

Criado por **Junior de Brito** - 2026

## 🤝 Contribuições

Contribuições são bem-vindas! Por favor, abra uma issue ou pull request.

---

**⭐ Se este repositório foi útil, considere deixar uma star!**
