<template>

  <head>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.1/css/all.min.css">
    <!-- <meta charset="UTF-8"> -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
  </head>
  <div class="main">
    <div class="section header">
      <div class="title"><img class="ToolEQA-icon" src="/snmp工具集成.png">ToolEQA</div>
      <div class="subtitle">
        Multi-Step Reasoning for Embodied Question Answering via Tool Augmentation
      </div>

      <div class="author-list">
        <span class="author">
          <el-link href="https://zmling22.github.io/">Mingliang Zhai</el-link>
          <span class="ind">1,2 &#9733;</span>,
        </span>
        <span class="author">
          Hansheng Liang
          <span class="ind">3 &#9733;</span>,
        </span>
        <span class="author">
          Xiaomeng Fan
          <span class="ind">1 &#9733;</span>,
        </span>
        <span class="author">
          Zhi Gao
          <span class="ind">1</span>,
        </span>
        <span class="author">
          Chuanhao Li
          <span class="ind">4</span>,
        </span>
        <span class="author">
          Che Sun
          <span class="ind">2</span>,
        </span>
        <span class="author">
          Xu Bin
          <span class="ind">3</span>,
        </span>
        <span class="author">
          Yuwei Wu
          <span class="ind">1,2</span>,
        </span>
        <span class="author">
          Yunde Jia
          <span class="ind">2</span>,
        </span>
        <br>
      </div>
      <div class="author-list">
        <span class="org">
          <span class="ind">1</span>
          Beijing Key Laboratory of Intelligent Information Technology, Beijing Institute of Technology
        </span>
        <br>
        <span class="org">
          <span class="ind">2</span>
          Guangdong Laboratory of Machine Perception and Intelligent Computing, Shenzhen MSU-BIT University
        </span>
        <br>
        <span class="org">
          <span class="ind">3</span>
          School of Mechanical Engineering, Beijing Institute of Technology
        </span>
        <br>
        <span class="org">
          <span class="ind">4</span>
          Shanghai Artificial Intelligence Laboratory
        </span>
      </div>
      <span class="link-block">
        <a href="https://arxiv.org" class="external-link button is-normal is-rounded is-dark">
          <span class="icon">
            <svg xmlns="http://www.w3.org/2000/svg" width="1.0em" height="1.0em" viewBox="0 0 24 24">
              <path fill="currentColor"
                d="M3.842 0a1 1 0 0 0-.922.608c-.153.369-.044.627.294 1.111l6.919 8.36l-1.023 1.106a1.04 1.04 0 0 0 .003 1.423l1.23 1.313l-5.44 6.444c-.28.3-.453.823-.297 1.199a1.025 1.025 0 0 0 .959.635a.91.91 0 0 0 .689-.34l5.783-6.126l7.49 8.005a.85.85 0 0 0 .684.26a.96.96 0 0 0 .877-.615c.158-.377-.017-.75-.306-1.14L13.73 13.9l1.064-1.13a.963.963 0 0 0 .009-1.316L4.633.464S4.26.01 3.867 0zm0 .272h.017c.218.005.487.272.564.364l.005.006l.005.005l10.17 10.99a.69.69 0 0 1-.008.946l-1.066 1.133l-1.498-1.772l-8.6-10.39c-.328-.472-.352-.619-.26-.841a.73.73 0 0 1 .671-.44Zm14.341 1.57a.88.88 0 0 0-.655.242l-5.696 6.158l1.694 1.832l5.309-6.514c.325-.433.479-.66.325-1.029a1.12 1.12 0 0 0-.977-.689m-7.655 12.282l1.318 1.414l-5.786 6.13a.65.65 0 0 1-.496.26a.75.75 0 0 1-.706-.467c-.112-.269.036-.687.244-.909l.005-.005l.005-.006z" />
            </svg>
          </span>
          <span>arXiv (comming soon)</span>
        </a>
      </span>
      <span class="link-block">
        <a href="https://github.com/ToolEQA/ToolEQA" class="external-link button is-normal is-rounded is-dark">
          <span class="icon">
            <i class="fab fa-github"></i>
          </span>
          <span>Code</span>
        </a>
      </span>

      <!-- Data Link. need changing -->
      <span class="link-block">

        <a target="_blank" href="https://huggingface.co/datasets"
          class="external-link button is-normal is-rounded is-dark">
          <span class="icon">
            <i class="fa fa-database"></i>
          </span>
          <span>Data (comming soon)</span>
        </a>
      </span>

    </div>

    <div class="tldr">
      <p><b>TL;DR</b> 
        We introduce ToolEQA, an agent that integrates external tools with multi-step reasoning, where external tools can provide more useful information for completing the task, helping the model derive better exploration directions in the next step of reasoning and thus obtaining additional effective information. 
        This enables ToolEQA to generate more accurate responses with a shorter exploration distance.
        To enhance the model's ability for tool-usage and multi-step reasoning, we further design a novel EQA data generation pipeline that automatically constructs large-scale EQA tasks with reasoning trajectories and corresponding answers.
        </p>
    </div>

    <div class="section">
      <div class="video-wrapper">
        <iframe width="560" height="315" src="https://www.youtube.com/embed/qTHHB2ATnVc?si=-FimKZAu9a7QdocN" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
      </div>
    </div>
    
    <div class="section">
      <div class="section-title">Introduction</div>
      <p class="intro">
        Embodied Question Answering (EQA) requires agents to explore 3D environments to obtain observations and answer questions related to the scene.
        Existing methods leverage VLMs to directly explore the environment and answer questions without explicit thinking or planning, which limits their reasoning ability and results in excessive or inefficient exploration as well as ineffective responses.
        In this paper, we introduce ToolEQA, an agent that integrates external tools with multi-step reasoning, where external tools can provide more useful information for completing the task, helping the model derive better exploration directions in the next step of reasoning and thus obtaining additional effective information. 
        This enables ToolEQA to generate more accurate responses with a shorter exploration distance.
        To enhance the model's ability for tool-usage and multi-step reasoning, we further design a novel EQA data generation pipeline that automatically constructs large-scale EQA tasks with reasoning trajectories and corresponding answers.
        Based on the pipeline, we collect the EQA-RT dataset that contains about 18K tasks, divided into a training set EQA-RT-Train, and two test sets EQA-RT-Seen (scenes overlapping with the training set) and EQA-RT-Unseen (novel scenes).
        Experiments on EQA-RT-Seen and EQA-RT-Unseen show that ToolEQA improves the success rate by 9.2% ~ 20.2% over state-of-the-art baselines, while outperforming the zero-shot ToolEQA by 10% in success rate. 
        In addition, ToolEQA also achieves state-of-the-art performance on the HM-EQA, OpenEQA, and EXPRESS-Bench datasets, demonstrating its generality.
      </p>
    </div>

    <div class="section">
      <el-card class="teaser">
        <el-image src="./workflow.png"></el-image>
        <figcaption class="figcaption">Figure 1 — Overview of the ToolEQA agent workflow.</figcaption>
      </el-card>
    </div>

    <div class="section">
      <div class="section-title">Method</div>
        <div class="intro">
          To enable the agent to reason and act in complex environments, we propose a ToolEQA agent that integrates tool-usage strategies for the reasoning process. 
          ToolEQA conducts step-by-step reasoning on past observations and, at each step, generates corresponding thoughts and code to execute tools.
          Code offers greater flexibility than formats such as JSON for handling diverse inputs and outputs.
          As shown in Figure 2, ToolEQA comprises three components: 
          - a planner for generating overall task plan </br>
          - a controller for generating thought and code
          - an executor for executing code in environment
        </div>
      <br>
      <el-card class="teaser">
        <el-image src="./datapipeline.png"></el-image>
        <figcaption class="figcaption">Figure 2 — EQA-RT Data Generation Pipeline.</figcaption>
      </el-card>
    </div>

    <div class="section">
      <div class="section-title">Dataset Construction</div>
      <p class="intro"> 
        Our goal is to generate a large set of diverse, practical, and complex EQA tasks. 
        We first apply a 3D detection model to obtain each object's bounding box, position, and category, and sample the object image from detected objects.
        The object attributes and corresponding visual information are then fed into GPT-4o along with example question-answer pairs designed from brainstorming to simulate natural home conversations. 
        Guided by the prompt, GPT-4o generates questions and answers across six types: relationship, status, distance, location, counting, and attribute, where location is divided into two subcategories `location-location' and `location-special', and attribute is divided into three subcategories `color', `special', and `size'. 
        The answers are open-ended or multiple-choice, enabling the evaluating different capabilities of agents.
      </p>

      <el-card class="teaser">
        <el-image src="./stats/data_stat.png"></el-image>
        <figcaption class="figcaption">Figure 3 — Data statistics of the training set (EQA-RT-Train) and two test sets (EQA-RT-Seen and EQA-RT-Unseen). The scenes in EQA-RT-Seen have the overlap with EQA-RT-Train, while the scenes in EQA-RT-Unseen are not present in the training set.</figcaption>
      </el-card>

      <p class="intro"> 
        The dataset exhibits a pronounced long-tail distribution in both the average exploration steps and the number of related objects per question. 
        Most questions require around ten exploration steps; among them, 10,224 involve a single target, 7,098 involve two targets, and 940 involve three or more objects. 
        Figure 4(c) further compares EQA-RT-Seen and EQA-RT-Unseen in terms of the average number of objects per question, revealing that EQA-RT-Seen involves more objects. Since object count reflects task difficulty, this suggests that tasks in EQA-RT-Seen are more challenging.
      </p>

      <el-card class="teaser">
        <el-image src="./stats/data_stat2.png"></el-image>
        <figcaption class="figcaption">Figure 4 — Dataset statistic about steps count, objects count and the difference between two test set.</figcaption>
      </el-card>
    </div>

    <div class="section">
      <div class="section-title">Evaluation and Results </div>
      <div class="intro">
        As shown in Table 1 and Table 2, we report the performance of different methods on EQA-RT-Seen and EQA-RT-Unseen. Our ToolEQA consistently outperforms reasoning-inefficient methods Explore-EQA~\citep{ren2024explore} and Memory-EQA~\citep{zhai2025memory} across all metrics, demonstrating its effectiveness in tackling complex tasks.
        The comparison between agents equipped with fine-tuned and non-fine-tuned VLMs further validates the effectiveness of our data generation pipeline.
        The success rate of fine-tuned Qwen2.5VL-7B compared to the original Qwen2.5VL-7B on EQA-RT-Unseen improved from 45.1 to 56.1, the recall rate increased from 0.17 to 0.24, and $e_{path}$ improved from 0.2 to 0.32.
        Compared with the non-fine-tuned Qwen2.5-VL-7B, ToolEQA with GPT-4o achieves better performance, indicating that the controller’s capability directly determines the performance of ToolEQA. 
        However, the fine-tuned Qwen2.5-VL-7B surpasses GPT-4o in $e_{path}$ and success rate, while achieving comparable recall. 
        This indicates that our training has enabled the VLM to learn how to think and solve problems more effectively in indoor scenarios.
        <br>
      </div>

      <el-card class="stats-img-1">
        <el-image src="./results/main1.png"></el-image>
        <figcaption class="figcaption">Table 1 — Baseline evaluation on EQA-RT-Seen.</figcaption>
        <el-image src="./results/main2.png"></el-image>
        <figcaption class="figcaption">Table 2 — Baseline evaluation on EQA-RT-Unseen.</figcaption>
      </el-card>
    </div>

    <div class="section">
      <div class="section-title">Visualization </div>
      <div class="intro">
        As shown in Figure 5, the decision-making process integrates spatial layout, functional space, and environmental cues to guide navigation toward the target object (towels). Each step is supported by clear reasoning, such as moving forward to approach potential bathroom space, turning right to explore a promising corridor, or turning left after excluding non-target rooms. This information-driven and reasoning-based decision paradigm ensures that the generated exploration trajectory maintains a high degree of proximity to the ground-truth trajectory, effectively validating the rationality and effectiveness of the decision-making framework in target-oriented spatial exploration tasks.
      </div>

      <el-card class="stats-img-1">
        <el-image src="./results/visual1.png"></el-image>
        <figcaption class="figcaption">Figure 5 — Illustration of how explicit reasoning guides efficient exploration, enabling ToolEQA to answer questions faster and more accurately.</figcaption>
      </el-card>

      <div class="intro">
        Figure 6 highlights the clear advantage of tool-driven reasoning over direct Visual-Language Model (VLM) inference. Without tools, VLM often fails to localize objects precisely or distinguish fine-grained attributes such as size. In contrast, by integrating these specialized tools, our method obtained critical, fine-grained information (precise object localization, clutter-free cropping, and accurate size identification) that cannot be reliably captured by direct VLM inference on unprocessed images. This structured tool usage ensured the final comparison concluding that ``The chair has smaller volume'' was grounded in objective data, ultimately achieving a more accuracy response than would be possible with VLM alone.
      </div>
      <el-card class="stats-img-1">
        <el-image src="./results/visual2.png"></el-image>
        <figcaption class="figcaption">Figure 6 — Demonstration that the visual tools outperforms direct VLM inference without tools by accurately localizing, and comparing object volume.</figcaption>
      </el-card>
    </div>

  </div>

  <section class="section" id="BibTeX" style="text-align: left;">
    <div class="container is-max-desktop content" style="max-width: 100%; margin: 0 auto;">
      <h3 class="title" style="font-size: small;">
        BibTeX
      </h3>
      <div class="bibtex-container">
        <pre><code class="language-bibtex">@inproceedings{xxx,
  title={xxx},
  author={xxx},
  booktitle={xxx}
}
</code></pre>
      </div>
    </div>
  </section>


  <div class="footer">
    This website is inspired by <el-link href="https://mathvista.github.io/">MathVista</el-link> and <el-link
      href="https://nerfies.github.io/">Nerfies</el-link>.
  </div>
</template>

<script setup>
import Dialog from './Dialog.vue'

import { onMounted, ref } from 'vue'

const dataset1 = ref([])
const loadData1 = async () => {
  const resp1 = await fetch('./data/demo-100k.json')
  dataset1.value = await resp1.json()
}

const dataset2 = ref([])
const loadData2 = async () => {
  const resp2 = await fetch('./data/demo-1m.json')
  dataset2.value = await resp2.json()
}

const dataset3 = ref([])
const loadData3 = async () => {
  const resp3 = await fetch('./data/demo-bench.json')
  dataset3.value = await resp3.json()
}

onMounted(() => {
  loadData1(),
    loadData2(),
    loadData3()
})
</script>






<style scoped>
.main {
  text-align: center;
  color: #333;
}

.header {
  margin: 60px 0 0 0 !important;
}

.title {
  font-size: 5em;
}

.subtitle {
  font-size: 2.5em;
  color: #555;
}

.author-list {
  margin-top: 20px;
}

.author a {
  font-size: 1.2em;
  font-weight: normal;
  color: #337ecc;
}

.org {
  margin: 0 4px 0 4px;
}

.ind {
  font-size: 0.8em;
  vertical-align: super;
}

.section {
  margin: 50px 0;
}

.tldr {
  text-align: left;
  font-size: 1em;
  max-width: 1360px;
  line-height: 150%;
}

.section-title {
  margin: 20px;
  font-size: 2em;
  font-weight: bold;
}

.conference {
  text-align: center;
  margin: 20px;
  font-size: 1.5em;
  color: #665;
}

.uns {
  text-decoration: underline;
}

.mat-icon {
  width: 0.8em;
  height: 0.8em;
  margin-right: 0.2em;
}

.teaser {
  max-width: 960px;
  margin: 0 auto;
}

.stats-img {
  height: 300px;
}

.stats-img-1 {
  max-width: 67%;
  max-height: 95%;
  object-fit: contain;
  margin: 0 auto;
  display: block;
}

.intro {
  text-align: justify;
  font-size: 1em;
  max-width: 1360px;
  line-height: 150%;
}

.link-block a {
  margin-top: 5px;
  margin-bottom: 5px;
}

.example-dialog {
  width: 800px;
}

.footer {
  color: #aaa;
  margin: 100px 0 60px 0;
}


/* The top button */
.external-link {
  display: inline-block;
  padding: 8px 16px;
  /* inner margin */
  margin: 4px;
  /* outer margin */
  border: 1px solid #9a9c9e;
  /* color of border */
  border-radius: 9px;
  background-color: #8a8b8b;
  color: white;
  text-decoration: none;
  font-size: 20px;
  transition: background-color 0.3s;
}
.conference {
  text-align: center;
  margin: 20px;
  font-size: 1.5em;
  color: #665;
}
.external-link:hover {
  background-color: #8e8f90;
}

.external-link .icon {
  margin-right: 8px;
}

.external-link .fas {
  font-size: 18px;
}

.bibtex-container {
  background-color: #e1e4e9;
  /* Change background color to match the theme */
  padding: 1em;
  /* Add padding for better readability */
  border-radius: 5px;
  /* Add border radius for rounded corners */
  text-align: left;
  white-space: pre;
  /* Preserve formatting and prevent line breaks */
  overflow-x: auto;
  /* Add horizontal scroll bar */
}

.video-wrapper {
  max-width: 1440px;
  margin: 0 auto;
  /* 16:9 响应式容器 */
  position: relative;
  padding-bottom: 56.25%;
  height: 0;
  overflow: hidden;
}
.video-wrapper video,
.video-wrapper iframe {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  border-radius: 6px;
  background: #000;
}
/* 小屏幕可选微调 */
@media (max-width: 480px) {
  .section-title { font-size: 1.2em; }
}

pre {
  margin: 0;
}

code {
  font-family: 'Courier New', Courier, monospace;
  /* Change font to monospace */
  color: #0a0b0b;
  /* Change text color to match the theme */
}
</style>
