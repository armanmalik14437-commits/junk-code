/* PARTICLES */
// Create a global gsap timeline that contains all tweens
const tl = gsap.timeline({
  repeat: -1,
  yoyo: true
});

const path = document.querySelector("path");
const length = path.getTotalLength();
const vertices = [];
for (let i = 0; i < length; i += 0.1) {
  const point = path.getPointAtLength(i);
  const vector = new THREE.Vector3(point.x, -point.y, 0);
  vector.x += (Math.random() - 0.5) * 30;
  vector.y += (Math.random() - 0.5) * 30;
  vector.z += (Math.random() - 0.5) * 70;
  vertices.push(vector);
  // Create a tween for that vector
  tl.from(vector, {
    x: 500 / 2, // Center x of the heart
    y: -552 / 2, // Center y of the heart
    z: 0, // center of the scene
    ease: "power2.inOut",
    duration: "random(2, 5)" // Random duration
  },
  i * 0.002 // Delay calculated from the distance along the path
  );
}
