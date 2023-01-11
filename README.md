useFrame is invoked just before the current frame is rendered to the canvas and with default canvas setting useFrame is called 60 times per second (60fps)

setting !rotate works like a flipswitch between true and false


continuity of state ---->

We are not using the <boxGeometry /> tag in the JSX anymore, but instantiating a new THREE.BoxGeometry and appending it to the props in the mesh tag instead.

This appears to work exactly the same. But there is a problem. This is a very small application, so in any case, the problem is likely to go unnoticed. But however, it is there.

This Box function will be re-executed every time there is a state change. This means that it will unnecessarily re-create a new THREE.BoxGeometry() every time it's called.

Click on a Box and you will see that its geometry's uuid is changing. This means that it is a new instance of a THREE.BoxGeometry in memory and being rendered to the scene. Creating new objects unnecessarily is not recommended.

We can solve this problem by using the useMemo hook. useMemo will act as cache for the geometry and return that instead of generating a new object.

useMemo will cause the inner function to only run when needed. Use useMemo when you want to keep expensive, resource intensive functions from needlessly re-running.


modulus ----> onPointerDown={() => setCount((count + 1) % 2)} //modulus 2 means it will either be a zero or 1 (0 + 1 / 2 remainder 1, 1 + 1 / 2 remainder 0)

geometry can be added as a prop to a mesh or a jsx tag inside mesh

lights lesson - to create a sun use a sphere inside your light source tag

<OrbitControls target={[0, 1, 0]} maxPolarAngle={Math.PI / 2} /> locks the camera inside the sphere so you cannot pan underneath the x plane

leva goes outside the canvas 

any HTML elements need to be placed outside the canvas

