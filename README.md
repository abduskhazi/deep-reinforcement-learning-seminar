# Deep RL Seminar: IMAGINE

**Paper**: [IMAGINE — Curiosity-Driven Exploration Using Language](https://arxiv.org/pdf/2002.09253.pdf) (ICML 2020)  
**Seminar** — University of Freiburg  
**Takeaway**: Language as a goal interface enables generalization — but the "perfect social partner" assumption is the real bottleneck.

---

## The Paradigm Shift
```
Standard RL: Human engineers a reward function per task
IMAGINE:     Agent invents goals using language; social partner only *describes* outcomes
```

---

## Architecture (Condensed)
```
Goal Generator (50% known / 50% imagined via atom swap)
        │
        ▼
LSTM Encoder → Goal Embedding (g)
        │
        ▼
┌─────────────────────────────────────────┐
│ π(a|s,g)  │  Q(s,a,g)  │  R(s,g)       │
│ Policy    │  Critic    │  Reward (bin)  │
└─────────────────────────────────────────┘
        │
        ▼
Playground Env (2D grid, grasp/grow/go)
        │
        ▼
Social Partner: "Grasp red cat" → describes actual outcome
        │
        ▼
Reward Memory: (1, achieved) + (0, known_but_failed)
HER Memory: trajectories relabeled with actual goals
        │
        ▼
Retrain all three → Repeat
```

---

## Why Generalization Works
Language composes: "Grow red furniture" = known verb "Grow" + known adjective "red" + known noun "furniture". The agent recombines embeddings — it doesn't need to see every combination.

---

## The Cheat Code (What The Paper Doesn't Solve)
The "Social Partner" is a perfect oracle: always describes outcomes in the agent's vocabulary, never ambiguous, never inconsistent. Real humans are none of those things. That's the open problem — and where I'd take this next.

---

## Generalization Results (From Paper)
| Unseen Goal | Behavior |
|-------------|----------|
| **Grow red furniture** | Brings food/water to chair (like child feeding doll) — verb transfers |
| **Grow any plant** | Tries food+water, discovers only water works, adapts via HER |

---

## Repo Contents
| Path | What |
|------|------|
| `Abstract/Abstract.tex` | Full technical summary (my write-up) |
| `summary/` | Extended analysis + figures |
| `presentation.pptx` | Seminar slides (5 MB) |

---

**Author**: Abdus Salam Khazi  
**Contact**: abduskhazi@gmail.com