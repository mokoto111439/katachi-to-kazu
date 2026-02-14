let selectedShape = "";

const messages = {
  "circle-5": "揺れは悪くありません。巡り直す合図です。",
  "triangle-8": "進む力はあります。あとは向きを決めるだけ。",
  "square-4": "積み重ねたものが、静かに支えています。"
  // 他の24通りもここに追加
};

function showStep(id) {
  document.querySelectorAll(".step").forEach(s => s.classList.remove("active"));
  document.getElementById(id).classList.add("active");
}

document.querySelectorAll(".shape").forEach(el => {
  el.addEventListener("click", () => {
    selectedShape = el.dataset.shape;
    showStep("step-number");
  });
});

document.querySelectorAll(".numbers button").forEach(btn => {
  btn.addEventListener("click", () => {
    const key = `${selectedShape}-${btn.dataset.number}`;
    document.getElementById("result-text").textContent =
      messages[key] || "静かな流れが、そっとあります。";
    showStep("step-result");
  });
});

document.getElementById("retry").addEventListener("click", () => {
  showStep("step-shape");
});
