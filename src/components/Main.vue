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
          <span class="ind">3 &#9733;
        </span>
        <span class="author">
          Xiaomeng Fan
          <span class="ind">&#9993;1</span>,
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
          <span class="ind">1</span>,
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
          School of Computer, Beijing Institute of Technology
        </span>
        <br>
        <span class="org">
          <span class="ind">2</span>
          Guangdong Laboratory of Machine Perception and Intelligent Computing, Shenzhen MSU-BIT University
        </span>
        <br>
        <span class="org">
          <span class="ind">2</span>
          School of Mechanical Engineering, Beijing Institute of Technology
        </span>
        <br>
        <span class="org">
          <span class="ind">2</span>
          Shanghai Artificial Intelligence Laboratory
        </span>
      </div>

      <span class="link-block">
        <a href="https://arxiv.org/pdf/2505.13948" class="external-link button is-normal is-rounded is-dark">
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

        <a target="_blank" href="https://huggingface.co/datasets/zmling/MT-HM3D"
          class="external-link button is-normal is-rounded is-dark">
          <span class="icon">
            <i class="fa fa-database"></i>
          </span>
          <span>Data (comming soon)</span>
        </a>
      </span>

      <!-- <span class="link-block">
        <a href="file/clova_cvpr24_poster.pdf"
            class="external-link button is-normal is-rounded is-dark">
          <span class="icon">
            <i class="fas fa-file-pdf"></i>
          </span>
          <span>Submited to ICLR 2026</span>
        </a>
      </span> -->

      <!-- <span class="link-block">
            <a href="file/clova_slides.pdf"
               class="external-link button is-normal is-rounded is-dark">
              <span class="icon">
                  <i class="fas fa-file-pdf"></i>
              </span>
              <span>Slides</span>
            </a>
          </span> -->

    </div>

    <div class="tldr">
      <p><b>TL;DR</b> 
        We introduce \textbf{ToolEQA}, an agent that integrates external tools with multi-step reasoning, where external tools can provide more useful information for completing the task, helping the model derive better exploration directions in the next step of reasoning and thus obtaining additional effective information. 
        This enables ToolEQA to generate more accurate responses with a shorter exploration distance.
        To enhance the model's ability for tool-usage and multi-step reasoning, we further design a novel EQA data generation pipeline that automatically constructs large-scale EQA tasks with reasoning trajectories and corresponding answers.
        </p>
    </div>

    <div class="section">
      <el-card class="teaser">
        <el-image src="./teaser.png"></el-image>
      </el-card>
    </div>


    <div class="section">
      <div class="section-title">Introduction</div>
      <p class="intro">
        Embodied Question Answering (EQA) requires agents to explore 3D environments to obtain observations and answer questions related to the scene.
        Existing methods leverage VLMs to directly explore the environment and answer questions without explicit thinking or planning, which limits their reasoning ability and results in excessive or inefficient exploration as well as ineffective responses.
        In this paper, we introduce \textbf{ToolEQA}, an agent that integrates external tools with multi-step reasoning, where external tools can provide more useful information for completing the task, helping the model derive better exploration directions in the next step of reasoning and thus obtaining additional effective information. 
        This enables ToolEQA to generate more accurate responses with a shorter exploration distance.
        To enhance the model's ability for tool-usage and multi-step reasoning, we further design a novel EQA data generation pipeline that automatically constructs large-scale EQA tasks with reasoning trajectories and corresponding answers.
        Based on the pipeline, we collect the EQA-RT dataset that contains about 18K tasks, divided into a training set EQA-RT-Train, and two test sets EQA-RT-Seen (scenes overlapping with the training set) and EQA-RT-Unseen (novel scenes).
        Experiments on EQA-RT-Seen and EQA-RT-Unseen show that ToolEQA improves the success rate by 9.2$\sim$20.2\% over state-of-the-art baselines, while outperforming the zero-shot ToolEQA by 10\% in success rate. 
        In addition, ToolEQA also achieves state-of-the-art performance on the HM-EQA, OpenEQA, and EXPRESS-Bench datasets, demonstrating its generality.
      </p>
    </div>

    <div class="section">
      <div class="section-title">Method</div>
        <div class="intro">
          Given the input question and agent observation, we first update the hierarchical memory. 
          Subsequently, question-relevant memories are retrieved through the memory retriever and injected into the respective modules.
          We concatenate the memories and the question, which are then fed into the planner to determine the next navigation point. 
          Once the agent arrives at a navigation point, it assesses whether to halt its journey. If the decision is `No', the process loops back to 
          the memory update step; if `Yes', the agent responds to the question.
        </div>
      <br>
      <el-card class="teaser">
        <el-image src="./framework.png"></el-image>
      </el-card>
    </div>



    <div class="section">
      <div class="section-title">Dataset Construction</div>
      <p class="intro"> 
        To evaluate memory ability of the models, we propose an multi-target EQA dataset based on HM3D. 
        We first sample 5 to 10 images from the scene using the Habitat simulator. And then we input the sampled images and prompt the GPT-4o select multiple related 
        objects from those images, specifying the output format to obtain raw data.
        For filter the raw data, we use GPT-4-mini to removing illogical question-answer pairs, and generate diverse QA data.
        Finally, we manually verify the correctness of the data to ensure that the questions can be answered within the embodied environment.
        Through the above steps, we constructed 1587 QA pairs of 4 types, and the statistical information is shown in figure.
      </p>

      <el-card class="teaser">
        <el-image src="./stats/data.jpg"></el-image>
      </el-card>

    </div>

    <div class="section">
      <div class="section-title">Evaluation and Results </div>
      <div class="intro">
        We evaluate the <b>MemoryEQA</b> on three dataset: <b>MT-HM3D</b>, <b>GAIA</b> and <b>OpenEQA</b>. 
        The results show that the MemoryEQA achieves improvements on all datasets, which
        outperforms baseline by 19.8% on MT-HM3D, showing the effectiveness of the proposed framework, leading to obtain
        better memory capabilities.
        <br>
      </div>

      <div class="intro">
        <b>Metric.</b> 
        In the <b>MT-HM3D</b> and <b>HM-EQA</b> dataset, we measure two metrics for agents, including
        <i><b>Succ. (Success Rate)</b></i>, and <i><b>Step (Normalization Step)</b></i>. 
        <i><b>Succ.</b></i> measures the correctness of predicted answers. 
        <i><b>Step</b></i> means the efficiency of exploration. 
        In the <b>OpenEQA</b>, we use three metrics for agents, including <i><b>GPT Score</b></i>, <i><b>ROUGE_L</b></i> and <i><b>Step (Normalization Step)</b></i>.
        <i><b>GPT Score</b></i> measures the correctness of predicted answers.
        <i><b>ROUGE_L</b></i> measures the similirity between predicted open-vocabulary answers and ground-truth answers.
        <br>
      </div>

      <div class="intro">
        <b>Results.</b> 
        On MT-HM3D, MemoryEQA attains a success rate of 54.5%, outperforming baseline by 18.9% (Exp.3), highlighting the critical role of hierarchical memory in multi-target tasks. 
        The results demonstrate that MemoryEQA exhibits superior performance in multi-modal reasoning tasks, particularly in complex scene understanding and knowledge integration.
        The analysis of experimental results across Exp.1-3, Exp.4-5, and Exp.6-7 reveals a significant positive correlation between the performance of the VLM and the effectiveness 
        of the EQA system. This observation underscores the critical role that VLM plays in enhancing the EQA system's ability to process and interpret complex queries within visual 
        environments. As the VLM's accuracy and understanding improve, so does the EQA system's capacity to deliver precise and contextually relevant answers, demonstrating a synergistic 
        relationship between the two components. This finding highlights the importance of advancing VLM capabilities to further boost the overall performance of EQA systems in practical 
        applications.
        <br>
      </div>
      <el-card class="stats-img-1">
        <el-image src="./results/result.png"></el-image>
      </el-card>
      
    </div>

  </div>

  <section class="section" id="BibTeX" style="text-align: left;">
    <div class="container is-max-desktop content" style="max-width: 100%; margin: 0 auto;">
      <h3 class="title" style="font-size: small;">
        BibTeX
      </h3>
      <div class="bibtex-container">
        <pre><code class="language-bibtex">
    @inproceedings{gao2025multi,
      title={Memory-Centric Embodied Question Answering},
      author={Zhai, Mingliang and Gao, Zhi and Wu, Yuwei and Jia, Yunde},
      booktitle={arXiv preprint arXiv:2505.13948}
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
  max-width: 840px;
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
