# README: Etsy Recommender System Analysis

## 📊 Project Overview

This project provides a comprehensive analysis of Etsy's recommendation system, examining how the platform serves a unique two-sided marketplace of independent sellers and conscious consumers. Through scenario design analysis and hands-on reverse engineering, this study evaluates how Etsy's algorithms balance personalization with discovery in a marketplace built on uniqueness and craftsmanship.

## 🎯 Project Purpose

As part of my Master's in Data Science coursework at CUNY SPS (DATA 643 - Recommender Systems), this project demonstrates:

- **Scenario design thinking** for multi-stakeholder platforms (buyers AND sellers)
- **Reverse engineering** of production recommendation systems through interface observation
- **Strategic analysis** of content-based vs. collaborative filtering tradeoffs
- **User-centered design thinking** for recommendation improvements
- **Technical communication** skills for data science and product audiences

This analysis is particularly relevant for roles in personalization, machine learning, and marketplace optimization at e-commerce companies, two-sided platforms, and tech organizations building recommendation engines.

## 🎨 Why Etsy?

Unlike traditional e-commerce giants like Amazon, Etsy presents unique recommendation challenges:

- **Inventory uniqueness**: Many items are one-of-a-kind or limited quantity
- **Aesthetic diversity**: Highly subjective style preferences matter more than popularity
- **Two-sided optimization**: Must serve both buyer discovery AND seller visibility goals
- **Small seller ecosystem**: Algorithms must prevent winner-take-all dynamics
- **Emotional connection**: Buyers value authenticity, craft stories, and supporting artisans

These characteristics make Etsy an ideal case study for understanding how recommendation systems adapt to specialized marketplaces beyond mass retail.

## 📁 Repository Structure

```
etsy-recommender-analysis/
│
├── README.md                          # This file
├── etsy_analysis.Rmd                  # Main R Markdown analysis document
├── etsy_analysis.html                 # Rendered HTML output
│
├── Etsy/                              # Screenshots from reverse engineering
│   ├── item_for_cart.png             # Item added to cart
│   ├── item_in_carousel.png          # Same item appearing in recommendations
│   └── Backpacks_in_recommender.png  # "Picks inspired by your shopping"
│
└── references/
    ├── amazon_item_to_item_CF.pdf    # Amazon collaborative filtering paper
    └── nyt_recommendation_blog.pdf    # NYT recommendation system blog post
```

## 🔍 Analysis Framework

### 1. Scenario Design Analysis (Dual Perspective)

**Organization (Etsy):**
- Balancing marketplace health between buyers and sellers
- Key metrics: GMV (Gross Merchandise Value), conversion rates, seller success
- Platform sustainability through fair seller visibility

**Buyers (Primary Stakeholders):**
- **Demographics**: Gift shoppers, home decorators, craft enthusiasts, conscious consumers
- **Goals**: Discover unique items, find perfect gifts, support small businesses
- **Behavioral patterns**: Browse-heavy, inspiration-seeking, aesthetic-driven

**Sellers (Secondary Stakeholders):**
- **Profile**: Solo entrepreneurs, side hustlers, small business owners, vintage curators
- **Goals**: Get discovered, generate consistent sales, build customer relationships
- **Pain points**: Visibility in saturated categories, algorithm dependency, thin margins

### 2. Reverse Engineering Methodology

**Hands-On Observation:**
- Created fresh user account to observe cold start behavior
- Documented timeline: Personalized recommendations appeared **within 10 minutes**
- Tracked how interactions (favorites, cart adds, browsing) influenced recommendations
- Tested refresh behavior: Seasonal content prioritized over personalized recommendations
- Captured screenshots showing recommendation evolution

**Key Findings:**
- **Fast personalization**: Two carousels ("Dive back into these 10 finds" and "Picks inspired by your shopping") appeared after brief browsing
- **Dynamic reordering**: Favoriting items changed carousel ordering on refresh
- **Seasonal prioritization**: Holiday items moved to top after page refresh
- **Session-based adaptation**: Active browsing triggered more personalized recommendations

### 3. Algorithmic Architecture (Inferred)

**Primary Approach: Content-Based Filtering (80%)**

Rationale: Etsy's marketplace thrives on aesthetic uniqueness, making content attributes more valuable than collaborative popularity signals.

**Content-Based Features:**
- "More Like This" recommendations based on:
  - Visual similarity (color palettes, design aesthetic)
  - Material attributes (wood, metal, fabric, vintage)
  - Style clustering (bohemian, minimalist, industrial)
  - Price range matching
- Seasonal/occasion detection from search patterns
- Cross-category aesthetic connections (minimalist jewelry → minimalist home decor)
- Intentional serendipity (15% unexpected items to prevent filter bubbles)

**Secondary Approach: Collaborative Filtering (20%)**

Used for:
- "Shoppers Like You Also Bought" recommendations
- Cold start support for new users
- Trend validation across marketplace
- Popular items within niche categories

**Why This Balance Works:**
Content-based filtering respects Etsy's uniqueness while giving sellers with niche products fair visibility, avoiding the rich-get-richer dynamics of pure collaborative filtering.

### 4. Recommendations for Improvement

**User Control & Transparency:**
- **Interest selection interface**: Let users explicitly declare style preferences at onboarding
- **Explicit feedback mechanisms**: Thumbs up/down or "Show me more/less like this" buttons
- **Gift Mode toggle**: Separate gift browsing from personal preference profile

**Discovery & Fairness:**
- **"Discover New Sellers" option**: Temporarily prioritize small/new shops
- **Serendipity controls**: Let users adjust exploration vs. exploitation balance

**Technical Improvements:**
- **Stable recommendations**: Reduce drastic algorithm changes on page refresh
- **Session continuity**: Allow users time to review recommendations before reordering

## 🔑 Key Concepts & Terminology

### From Amazon's Item-to-Item Collaborative Filtering:
- **Item-to-item similarity**: Matching products based on co-purchase patterns
- **Scalability**: Handling millions of unique items efficiently
- **Offline vs. online computation**: Pre-computing similarities vs. real-time ranking
- **Sparse user vectors**: Most users interact with tiny fraction of catalog

### From NYT's Collaborative Topic Modeling:
- **Content-based filtering**: Using item attributes (not just user behavior)
- **Hybrid approaches**: Combining content features with collaborative signals
- **Cold start problem**: Recommending new items without interaction history
- **Serendipitous recommendations**: Intentional introduction of unexpected items
- **Fresh content handling**: New listings added daily by thousands of sellers

### Etsy-Specific Concepts:
- **Aesthetic-based matching**: Style/visual similarity over popularity
- **Two-sided marketplace optimization**: Balancing buyer and seller goals
- **Uniqueness challenge**: Many items are one-of-a-kind or limited inventory
- **Small seller visibility**: Preventing platform concentration on top sellers
- **Session-based personalization**: Rapid adaptation within single browsing session

## 🛠️ Methodology

- **Observational research**: Hands-on platform interaction as new user
- **Scenario design framework**: Multi-stakeholder analysis
- **Comparative analysis**: Benchmarking against documented approaches (Amazon, NYT)
- **Interface documentation**: Screenshot capture and annotation
- **Behavioral tracking**: Timeline of personalization emergence

## 📚 Key References

1. **Linden, G., Smith, B., & York, J.** (2003). "Amazon.com Recommendations: Item-to-Item Collaborative Filtering." *IEEE Internet Computing*, 76-80.

2. **Spangher, A.** (2015). "Building the Next New York Times Recommendation Engine." *The New York Times Open Blog*.

3. **Etsy Engineering Blog**: https://www.etsy.com/codeascraft/

4. **Etsy Search & Discovery Team publications** on marketplace ranking and personalization

## 💡 Key Findings Summary

**Strengths of Etsy's System:**
- ✅ **Rapid personalization**: Meaningful recommendations within 10 minutes of browsing
- ✅ **Content-focused approach**: Respects aesthetic diversity and uniqueness
- ✅ **Multiple recommendation surfaces**: Carousels, related items, seasonal promotions
- ✅ **Balance of signals**: Mix of personal preference and seasonal trends

**Areas for Improvement:**
- ⚠️ **Over-aggressive refresh**: Algorithm changes too drastically on page reload
- ⚠️ **Limited user control**: No explicit feedback or preference adjustment
- ⚠️ **Gift browsing contamination**: Gift shopping affects personal recommendations
- ⚠️ **New seller visibility**: Unclear how small shops compete for discovery
- ⚠️ **Transparency**: No explanations for why items are recommended

**Strategic Opportunities:**
- 🎯 Add explicit interest onboarding for better cold start
- 🎯 Implement Gift Mode to separate shopping contexts
- 🎯 Create "Discover New Sellers" feature for marketplace health
- 🎯 Provide feedback mechanisms (thumbs up/down) for active learning
- 🎯 Stabilize recommendations across page refreshes

## 👤 Author

**Candace Grant**  
MS Data Science Candidate | CUNY School of Professional Studies  
Multi-subject teacher at Academics West (Biology, Chemistry, Physics, Introduction to Coding)

**Background:**  
As an educator teaching multiple subjects across grade levels, I understand the importance of personalization that respects individual preferences while encouraging discovery—similar to how Etsy must balance showing buyers what they love while exposing them to new artisans and styles.

## 🎓 Course Information

**Course**: DATA 643 - Recommender Systems  
**Institution**: CUNY School of Professional Studies  
**Semester**: Fall 2024  
**Assignment**: Discussion 1 - Scenario Design & Reverse Engineering  
**Date**: November 6, 2025

## 📖 How to View This Analysis

### Option 1: View HTML Output (Recommended)
1. Download `etsy_analysis.html`
2. Open in any web browser
3. Interactive table of contents for easy navigation

### Option 2: Compile from Source
```r
# Install required packages
install.packages(c("rmarkdown", "knitr"))

# Render the R Markdown file
rmarkdown::render("etsy_analysis.Rmd")
```

### Option 3: Read R Markdown on GitHub
The `.Rmd` file can be viewed directly, though screenshots may render better in HTML.

## 🔗 Project Highlights

**Technical Skills Demonstrated:**
- Recommender system algorithm analysis (content-based vs. collaborative filtering)
- User research and behavioral observation
- Multi-stakeholder scenario design
- Interface reverse engineering
- Strategic product recommendations

**Business Acumen:**
- Two-sided marketplace dynamics
- Balancing competing stakeholder needs
- Ethical considerations (seller fairness, filter bubbles)
- User experience optimization

**Communication:**
- Technical writing for data science audiences
- Visual documentation (screenshots with annotations)
- Clear explanation of complex algorithms
- Actionable improvement recommendations

## 🔄 Project Status

**Status**: ✅ Complete  
**Version**: 1.0  
**Last Updated**: November 6, 2025

**Potential Extensions:**
- Quantitative analysis using Etsy's public API
- A/B testing framework design for recommendation improvements
- Comparative analysis: Etsy vs. Amazon vs. specialized marketplaces
- Deep dive into visual similarity algorithms for aesthetic matching
- Seller perspective analysis: How do algorithms affect small business success?

## 🌟 Why This Project Matters

Etsy represents a different paradigm in e-commerce recommendations:

- **Not just about scale**: Algorithms must serve uniqueness, not just efficiency
- **Ethical considerations**: Fair visibility for small sellers vs. pure optimization
- **Aesthetic intelligence**: Visual and stylistic understanding matters more than popularity
- **Community impact**: Recommendations affect livelihoods of independent artisans

Understanding how to build recommendation systems for specialized, values-driven marketplaces is increasingly important as consumers seek alternatives to mass retail and as platforms balance growth with community health.

## 📧 Connect & Discuss

Interested in discussing:
- Two-sided marketplace recommendation strategies
- Content-based vs. collaborative filtering tradeoffs
- Visual similarity and aesthetic matching algorithms
- Ethical considerations in recommendation system design
- Small business visibility in algorithmic marketplaces


---

## 📄 License

This project is created for educational purposes as part of graduate coursework. All screenshots are used for academic analysis under fair use. Etsy is a trademark of Etsy, Inc.

---

