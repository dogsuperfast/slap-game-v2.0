<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Floating Slap Arena</title>
  <style>
    * { box-sizing: border-box; }
    body {
      margin: 0;
      overflow: hidden;
      background: #101b32;
      color: white;
      font: 15px system-ui, sans-serif;
    }
    #hud {
      position: fixed;
      inset: 14px auto auto 14px;
      z-index: 2;
      width: 255px;
      padding: 12px 14px;
      background: #101828e8;
      border: 1px solid #ffffff2a;
      border-radius: 10px;
      line-height: 1.5;
      pointer-events: none;
    }
    #hud strong { color: #ffd166; }
    #leaderboard { margin-top: 8px; font-size: 13px; }
    #leaderboard div { display: flex; justify-content: space-between; }
    #help {
      position: fixed;
      inset: auto 0 22px;
      text-align: center;
      color: white;
      text-shadow: 0 2px 6px black;
      pointer-events: none;
    }
    #start {
      position: fixed;
      inset: 0;
      z-index: 3;
      display: grid;
      place-items: center;
      padding: 24px;
      text-align: center;
      background: #08111dcc;
      cursor: pointer;
    }
    #start > div {
      max-width: 500px;
      padding: 24px 30px;
      border: 1px solid #ffffff44;
      border-radius: 16px;
      background: #17243b;
    }
    #start h1 { margin-top: 0; color: #ffd166; }
    #notice {
      position: fixed;
      inset: 20% 0 auto;
      z-index: 2;
      text-align: center;
      font-size: 24px;
      font-weight: bold;
      color: #ffd166;
      text-shadow: 0 2px 8px black;
      pointer-events: none;
    }

    #codePanel[hidden] { display: none; }
    #codePanel {
      position: fixed;
      inset: 0;
      z-index: 5;
      display: grid;
      place-items: center;
      background: #08111dcc;
    }
    #codeBox {
      position: relative;
      width: min(300px, calc(100vw - 32px));
      padding: 22px;
      border: 1px solid #ffffff44;
      border-radius: 12px;
      background: #17243b;
      text-align: center;
    }
    #codeInput {
      width: 100%;
      margin: 10px 0;
      padding: 10px;
      border: 1px solid #ffffff55;
      border-radius: 6px;
      font: inherit;
    }
    #submitCode {
      padding: 8px 14px;
      border: 0;
      border-radius: 6px;
      background: #60a5fa;
      cursor: pointer;
    }
    #closeCode {
      position: absolute;
      top: 7px;
      right: 8px;
      width: 25px;
      height: 25px;
      border: 0;
      border-radius: 5px;
      background: #e5484d;
      color: white;
      font-weight: bold;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <div id="hud">
    <strong>FLOATING SLAP ARENA</strong>
    <div id="where">Arena</div>
    <div id="score">Your knock-offs: 0</div>
    <div id="slapCounter">Slaps: 0</div>
    <div id="killCounter">Total kills: 0</div>
    <div id="equipped">Glove: Dash</div>
    <div id="ability">Ability: Rocket Dash (E)</div>
    <div id="leaderboard"></div>
  </div>
  <div id="notice"></div>
  <div id="help">WASD / Arrow Keys move · Mouse look · Space jump · Click slap · E ability · T Time Stop · K Kinetic Overload · C code</div>

  <div id="start">
    <div>
      <h1>Floating Slap Arena</h1>
      <p>Fight the bots and avoid falling! If you fall off the island, you’ll drop for a moment before respawning in the lobby. Walk around the lobby, aim at a glove stand and click to equip it, then enter the portal to return.</p>
      <p><strong>Click to play</strong><br>Move: WASD or arrows · Jump: Space · Slap: Click · Ability: E</p>
      <p><strong>Press C anytime to enter a code.</strong></p>
    </div>
  </div>

  <div id="codePanel" hidden>
    <div id="codeBox">
      <button id="closeCode" type="button" aria-label="Close">X</button>
      <label for="codeInput">Enter code here</label>
      <input id="codeInput" type="text" placeholder="Enter code here" autocomplete="off">
      <button id="submitCode" type="button">Submit</button>
    </div>
  </div>

  <script type="module">
    import * as THREE from 'https://cdn.jsdelivr.net/npm/three@0.160.0/build/three.module.js';

    const scene = new THREE.Scene();
    scene.background = new THREE.Color(0x9bd5f4);
    scene.fog = new THREE.Fog(0x9bd5f4, 65, 145);

    const camera = new THREE.PerspectiveCamera(75, innerWidth / innerHeight, 0.1, 200);
    const renderer = new THREE.WebGLRenderer({ antialias: true });
    renderer.setSize(innerWidth, innerHeight);
    renderer.setPixelRatio(Math.min(devicePixelRatio, 2));
    renderer.shadowMap.enabled = true;
    renderer.shadowMap.type = THREE.PCFSoftShadowMap;
    document.body.appendChild(renderer.domElement);

    scene.add(new THREE.HemisphereLight(0xdff4ff, 0x4c543c, 2));
    const sun = new THREE.DirectionalLight(0xffefcf, 2.5);
    sun.position.set(-18, 30, 12);
    sun.castShadow = true;
    sun.shadow.mapSize.set(2048, 2048);
    sun.shadow.camera.left = -80;
    sun.shadow.camera.right = 80;
    sun.shadow.camera.top = 60;
    sun.shadow.camera.bottom = -60;
    scene.add(sun);

    const arenaRadius = 36;
    const floorY = 0.95;
    const lobbyCenter = new THREE.Vector3(120, 0, 0);
    const portalX = lobbyCenter.x;
    const portalZ = -11;
    const satelliteRadius = arenaRadius / 5;
    const satelliteDistance = arenaRadius + satelliteRadius + 10;
    const satelliteIslands = [];
    const bridgeAreas = [];

    const island = new THREE.Mesh(
      new THREE.CylinderGeometry(36, 36, 5, 64),
      new THREE.MeshStandardMaterial({ color: 0x68a84e, roughness: 0.95 })
    );
    island.position.y = -2.5;
    island.castShadow = true;
    island.receiveShadow = true;
    scene.add(island);

    const grass = new THREE.Mesh(
      new THREE.CylinderGeometry(35.85, 35.85, 0.35, 64),
      new THREE.MeshStandardMaterial({ color: 0x68a84e, roughness: 0.95 })
    );
    grass.position.y = 0.16;
    grass.receiveShadow = true;
    scene.add(grass);

    const islandDirections = [
      new THREE.Vector2(1, 0),
      new THREE.Vector2(-1, 0),
      new THREE.Vector2(0, 1),
      new THREE.Vector2(0, -1)
    ];

    for (const direction of islandDirections) {
      const islandX = direction.x * satelliteDistance;
      const islandZ = direction.y * satelliteDistance;

      satelliteIslands.push({ x: islandX, z: islandZ, radius: satelliteRadius });

      const smallIsland = new THREE.Mesh(
        new THREE.CylinderGeometry(satelliteRadius, satelliteRadius * 0.82, 2.8, 32),
        new THREE.MeshStandardMaterial({ color: 0x68a84e, roughness: 0.95 })
      );
      smallIsland.position.set(islandX, -1.065, islandZ);
      smallIsland.castShadow = true;
      smallIsland.receiveShadow = true;
      scene.add(smallIsland);

      const smallGrass = new THREE.Mesh(
        new THREE.CylinderGeometry(
          satelliteRadius - 0.15,
          satelliteRadius - 0.15,
          0.28,
          32
        ),
        new THREE.MeshStandardMaterial({ color: 0x68a84e, roughness: 0.95 })
      );
      smallGrass.position.set(islandX, 0.195, islandZ);
      smallGrass.receiveShadow = true;
      scene.add(smallGrass);

      const perpendicular = new THREE.Vector2(-direction.y, direction.x);
      const innerEdge = arenaRadius;
      const outerEdge = satelliteDistance - satelliteRadius;
      const bridgeGap = outerEdge - innerEdge;
      const bridgeLength = bridgeGap + 1.6;
      const bridgeWidth = 2.2;
      const bridgeSpacing = 3.2;
      const bridgeCenterDistance = (innerEdge + outerEdge) / 2;
      const bridgeAngle = Math.atan2(direction.x, direction.y);

      for (const side of [-1, 1]) {
        const offset = side * bridgeSpacing / 2;
        const bridgeX = direction.x * bridgeCenterDistance + perpendicular.x * offset;
        const bridgeZ = direction.y * bridgeCenterDistance + perpendicular.y * offset;

        const plank = new THREE.Mesh(
          new THREE.BoxGeometry(bridgeWidth, 0.35, bridgeLength),
          new THREE.MeshStandardMaterial({ color: 0x80552f, roughness: 0.9 })
        );

        plank.position.set(bridgeX, 0.16, bridgeZ);
        plank.rotation.y = bridgeAngle;
        plank.castShadow = true;
        plank.receiveShadow = true;
        scene.add(plank);

        bridgeAreas.push({
          x: bridgeX,
          z: bridgeZ,
          direction,
          perpendicular,
          length: bridgeLength,
          width: bridgeWidth
        });
      }
    }

    for (let i = 0; i < 17; i++) {
      const angle = i * Math.PI * 2 / 17;
      const rock = new THREE.Mesh(
        new THREE.DodecahedronGeometry(1.1 + (i % 3) * 0.35),
        new THREE.MeshStandardMaterial({ color: i % 2 ? 0x554b42 : 0x766858 })
      );
      rock.position.set(
        Math.cos(angle) * (18 + i % 4) * 3,
        -5.3 - (i % 3),
        Math.sin(angle) * (18 + i % 4) * 3
      );
      rock.rotation.set(i, i * 0.7, i * 0.3);
      rock.castShadow = true;
      scene.add(rock);
    }

    const lobbyPlatform = new THREE.Mesh(
      new THREE.CylinderGeometry(16, 14, 2, 48),
      new THREE.MeshStandardMaterial({ color: 0x65727c, roughness: 0.9 })
    );
    lobbyPlatform.position.set(lobbyCenter.x, -0.75, lobbyCenter.z);
    lobbyPlatform.receiveShadow = true;
    lobbyPlatform.castShadow = true;
    scene.add(lobbyPlatform);

    const lobbyFloor = new THREE.Mesh(
      new THREE.CylinderGeometry(15.95, 15.95, 0.25, 48),
      new THREE.MeshStandardMaterial({ color: 0x789f80, roughness: 0.9 })
    );
    lobbyFloor.position.set(lobbyCenter.x, 0.25, lobbyCenter.z);
    lobbyFloor.receiveShadow = true;
    scene.add(lobbyFloor);

    for (let i = 0; i < 18; i++) {
      const cloud = new THREE.Mesh(
        new THREE.SphereGeometry(1, 12, 8),
        new THREE.MeshStandardMaterial({
          color: 0xffffff,
          transparent: true,
          opacity: 0.7
        })
      );
      const angle = i * 2.4;
      const centerX = i % 2 ? 0 : lobbyCenter.x;
      cloud.position.set(
        centerX + Math.cos(angle) * (32 + (i % 4) * 3),
        8 + (i % 5) * 1.8,
        Math.sin(angle) * (32 + (i % 4) * 3)
      );
      cloud.scale.set(2.5 + (i % 3), 0.8, 1.6);
      scene.add(cloud);
    }

    const gloves = [
      { name: 'Dash',       color: 0xff4b4b, ability: 'Rocket Dash',    cost: 275 },
      { name: 'Thunder',    color: 0xffd43b, ability: 'Thunderclap',    cost: 165 },
      { name: 'Spring',     color: 0x53e8ff, ability: 'Sky Pop',        cost: 55 },
      { name: 'Magnet',     color: 0xff62cc, ability: 'Magnetic Pull',  cost: 385 },
      { name: 'Frost',      color: 0x7ea7ff, ability: 'Freeze',         cost: 0 },
      { name: 'Blink',      color: 0xb36aff, ability: 'Blink Forward',  cost: 220 },
      { name: 'Guard',      color: 0x65e38a, ability: 'Glove Guard',    cost: 330 },
      { name: 'Quake',      color: 0xff8a35, ability: 'Ground Quake',   cost: 440 },
      { name: 'Rush',       color: 0xf3f0e5, ability: 'Super Speed',    cost: 110 },
      { name: 'Springshot', color: 0x9bdb48, ability: 'Launch Target',  cost: 500 }
    ];

    const regularGlovesCount = gloves.length;
    const potatoGloveIndex = regularGlovesCount;

    gloves.push({
      name: 'Potato',
      color: 0xb77b45,
      ability: 'Potato Bomb',
      cost: 0
    });

    const adminGloveIndex = gloves.length;
    gloves.push({
      name: 'Wrath of the Admin',
      color: 0x9b59ff,
      ability: 'Admin Powers',
      cost: 0
    });

    const gloveUnlockOrder = gloves
      .slice(0, regularGlovesCount)
      .map((glove, index) => ({ index, cost: glove.cost }))
      .sort((a, b) => a.cost - b.cost)
      .map(item => item.index);

    function getNextGloveToUnlock() {
      return gloveUnlockOrder.find(index => !ownedGloves.has(index));
    }

    const SAVE_KEY = 'floatingSlapArenaSaveV1';

    let savedGame = {};
    try {
      savedGame = JSON.parse(localStorage.getItem(SAVE_KEY) || '{}') || {};
    } catch {
      savedGame = {};
    }

    const initialSlaps =
      Number.isSafeInteger(savedGame.slaps) && savedGame.slaps >= 0
        ? savedGame.slaps
        : 0;

    let totalPlayerKills =
      Number.isSafeInteger(savedGame.totalKills) && savedGame.totalKills >= 0
        ? savedGame.totalKills
        : 0;

    const ownedGloves = new Set([4]);
    if (Array.isArray(savedGame.ownedGloves)) {
      for (const index of savedGame.ownedGloves) {
        if (
          Number.isInteger(index) &&
          index >= 0 &&
          index < gloves.length &&
          index !== adminGloveIndex
        ) {
          ownedGloves.add(index);
        }
      }
    }

    const savedGloveIndex =
      Number.isInteger(savedGame.gloveIndex) &&
      ownedGloves.has(savedGame.gloveIndex)
        ? savedGame.gloveIndex
        : 4;

    function makeGloveModel(color, scale = 1) {
      const group = new THREE.Group();
      const material = new THREE.MeshStandardMaterial({ color, roughness: 0.5 });

      const cuff = new THREE.Mesh(
        new THREE.CylinderGeometry(0.13, 0.17, 0.26, 12),
        material
      );
      cuff.rotation.x = Math.PI / 2;
      cuff.position.z = 0.22;
      group.add(cuff);

      const palm = new THREE.Mesh(new THREE.BoxGeometry(0.38, 0.34, 0.34), material);
      palm.position.z = -0.02;
      group.add(palm);

      const thumb = new THREE.Mesh(new THREE.BoxGeometry(0.15, 0.22, 0.16), material);
      thumb.position.set(-0.2, -0.08, -0.02);
      thumb.rotation.z = -0.45;
      group.add(thumb);

      group.scale.setScalar(scale);
      return group;
    }

    function makePotatoGloveModel(scale = 1) {
      const group = new THREE.Group();

      const potatoMaterial = new THREE.MeshStandardMaterial({
        color: 0xb77b45,
        roughness: 0.95
      });
      const cuffMaterial = new THREE.MeshStandardMaterial({
        color: 0x68401f,
        roughness: 0.85
      });
      const spotMaterial = new THREE.MeshStandardMaterial({
        color: 0x573719,
        roughness: 1
      });

      const cuff = new THREE.Mesh(
        new THREE.CylinderGeometry(0.13, 0.17, 0.26, 12),
        cuffMaterial
      );
      cuff.rotation.x = Math.PI / 2;
      cuff.position.z = 0.22;
      group.add(cuff);

      const potato = new THREE.Mesh(
        new THREE.SphereGeometry(0.25, 16, 12),
        potatoMaterial
      );
      potato.scale.set(1.05, 0.78, 1.25);
      potato.position.z = -0.02;
      group.add(potato);

      for (const [x, y, z] of [
        [-0.12, 0.08, -0.22],
        [0.12, -0.04, -0.24],
        [0.02, 0.13, -0.18]
      ]) {
        const spot = new THREE.Mesh(
          new THREE.SphereGeometry(0.025, 8, 6),
          spotMaterial
        );
        spot.position.set(x, y, z);
        group.add(spot);
      }

      group.scale.setScalar(scale);
      return group;
    }

    const playerGlove = makeGloveModel(gloves[4].color);
    playerGlove.position.set(0.48, -0.38, -0.78);
    camera.add(playerGlove);

    const potatoPlayerGlove = makePotatoGloveModel();
    potatoPlayerGlove.position.set(0.48, -0.38, -0.78);
    potatoPlayerGlove.visible = false;
    camera.add(potatoPlayerGlove);

    scene.add(camera);

    const gloveStands = [];
    const gloveStandOrder = Array.from({ length: regularGlovesCount }, (_, index) => index)
      .sort((a, b) => gloves[a].cost - gloves[b].cost);

    for (let slot = 0; slot < regularGlovesCount; slot++) {
      const i = gloveStandOrder[slot];
      const angle = Math.PI * 0.12 + (slot / (regularGlovesCount - 1)) * Math.PI * 0.76;
      const x = lobbyCenter.x + Math.cos(angle) * 8;
      const z = Math.sin(angle) * 8 - 1;

      const pedestal = new THREE.Mesh(
        new THREE.CylinderGeometry(0.72, 0.92, 0.8, 16),
        new THREE.MeshStandardMaterial({
          color: 0x3c4656,
          metalness: 0.25,
          roughness: 0.65
        })
      );
      pedestal.position.set(x, 0.65, z);
      pedestal.castShadow = true;
      pedestal.receiveShadow = true;
      scene.add(pedestal);

      const displayGlove = makeGloveModel(gloves[i].color, 1.45);
      displayGlove.position.set(x, 1.65, z);
      displayGlove.rotation.y = Math.PI;
      displayGlove.traverse(obj => {
        if (obj.isMesh) {
          obj.castShadow = true;
          obj.userData.gloveIndex = i;
        }
      });
      scene.add(displayGlove);

      const ring = new THREE.Mesh(
        new THREE.TorusGeometry(0.95, 0.06, 8, 24),
        new THREE.MeshBasicMaterial({ color: gloves[i].color })
      );
      ring.rotation.x = Math.PI / 2;
      ring.position.set(x, 1.08, z);
      scene.add(ring);

      gloveStands.push({ index: i, x, z, displayGlove, ring, pedestal });
    }

    const potatoStand = new THREE.Group();
    potatoStand.position.set(lobbyCenter.x - 9, 0, lobbyCenter.z - 5);
    potatoStand.visible = false;

    const potatoPedestal = new THREE.Mesh(
      new THREE.CylinderGeometry(0.72, 0.92, 0.8, 16),
      new THREE.MeshStandardMaterial({
        color: 0x3c4656,
        metalness: 0.25,
        roughness: 0.65
      })
    );
    potatoPedestal.position.y = 0.4;
    potatoPedestal.castShadow = true;
    potatoPedestal.receiveShadow = true;
    potatoStand.add(potatoPedestal);

    const potatoDisplayGlove = makePotatoGloveModel(1.45);
    potatoDisplayGlove.position.y = 1.4;
    potatoDisplayGlove.traverse(obj => {
      if (obj.isMesh) {
        obj.castShadow = true;
        obj.receiveShadow = true;
      }
    });
    potatoStand.add(potatoDisplayGlove);

    const potatoRing = new THREE.Mesh(
      new THREE.TorusGeometry(0.95, 0.06, 8, 24),
      new THREE.MeshBasicMaterial({ color: 0xb77b45 })
    );
    potatoRing.rotation.x = Math.PI / 2;
    potatoRing.position.y = 0.83;
    potatoStand.add(potatoRing);

    scene.add(potatoStand);

    function updateGloveStandAppearance() {
      for (const stand of gloveStands) {
        const unlocked = ownedGloves.has(stand.index);

        stand.displayGlove.traverse(obj => {
          if (obj.isMesh) {
            obj.material.color.setHex(
              unlocked ? gloves[stand.index].color : 0x414653
            );
          }
        });

        stand.ring.material.color.setHex(
          unlocked ? gloves[stand.index].color : 0x414653
        );
        stand.pedestal.material.color.setHex(
          unlocked ? 0x3c4656 : 0x252a35
        );
      }
    }

    updateGloveStandAppearance();

    const portal = new THREE.Mesh(
      new THREE.TorusGeometry(1.55, 0.22, 12, 36),
      new THREE.MeshStandardMaterial({
        color: 0x54ddff,
        emissive: 0x178bb0,
        emissiveIntensity: 1.8
      })
    );
    portal.position.set(portalX, 2.1, portalZ);
    scene.add(portal);

    const portalCore = new THREE.Mesh(
      new THREE.CircleGeometry(1.35, 32),
      new THREE.MeshBasicMaterial({
        color: 0x3a9dff,
        transparent: true,
        opacity: 0.38,
        side: THREE.DoubleSide
      })
    );
    portalCore.position.set(portalX, 2.1, portalZ);
    scene.add(portalCore);

    const potatoRevealButton = new THREE.Mesh(
      new THREE.SphereGeometry(0.16, 16, 12),
      new THREE.MeshStandardMaterial({
        color: 0x168cff,
        emissive: 0x0755aa,
        emissiveIntensity: 1.6,
        roughness: 0.35
      })
    );
    potatoRevealButton.position.set(portalX + 1.45, 1.25, portalZ - 0.35);
    scene.add(potatoRevealButton);

    const buttonGlow = new THREE.Mesh(
      new THREE.TorusGeometry(0.25, 0.035, 8, 20),
      new THREE.MeshBasicMaterial({
        color: 0x168cff,
        transparent: true,
        opacity: 0.8
      })
    );
    buttonGlow.position.copy(potatoRevealButton.position);
    scene.add(buttonGlow);

    function isOnArenaPlatform(x, z) {
      if (Math.hypot(x, z) <= arenaRadius) return true;

      for (const island of satelliteIslands) {
        if (Math.hypot(x - island.x, z - island.z) <= island.radius) {
          return true;
        }
      }

      for (const bridge of bridgeAreas) {
        const dx = x - bridge.x;
        const dz = z - bridge.z;

        const along = dx * bridge.direction.x + dz * bridge.direction.y;
        const across = dx * bridge.perpendicular.x + dz * bridge.perpendicular.y;

        if (
          Math.abs(along) <= bridge.length / 2 &&
          Math.abs(across) <= bridge.width / 2
        ) {
          return true;
        }
      }

      return false;
    }

    function getSatelliteIslandIndexAt(x, z) {
      return satelliteIslands.findIndex(
        island => Math.hypot(x - island.x, z - island.z) <= island.radius
      );
    }

    function getIslandRadiusAt(x, z) {
      if (Math.hypot(x, z) <= arenaRadius) return arenaRadius;

      const satelliteIndex = getSatelliteIslandIndexAt(x, z);
      if (satelliteIndex !== -1) return satelliteIslands[satelliteIndex].radius;

      let nearestRadius = arenaRadius;
      let nearestDistance = Infinity;

      for (const island of satelliteIslands) {
        const distance = Math.hypot(x - island.x, z - island.z);
        if (distance < nearestDistance) {
          nearestDistance = distance;
          nearestRadius = island.radius;
        }
      }

      return nearestRadius;
    }

    const player = {
      id: 'you',
      name: 'You',
      pos: new THREE.Vector3(0, floorY, 0),
      vel: new THREE.Vector3(),
      grounded: true,
      ragdoll: 0,
      ragAngle: 0,
      ragdollSpin: new THREE.Vector3(),
      lastHitBy: null,
      kills: 0,
      isPlayer: true,
      inLobby: false,
      gloveIndex: savedGloveIndex,
      abilityCooldown: 0,
      shieldTime: 0,
      speedTime: 0,
      dashTime: 0,
      freezeTime: 0,
      fallingOut: false,
      fallTimer: 0,
      hitContacts: new Set(),
      potatoBombArmed: false
    };

    playerGlove.traverse(obj => {
      if (obj.isMesh) obj.material.color.setHex(gloves[player.gloveIndex].color);
    });

 playerGlove.visible = player.gloveIndex !== potatoGloveIndex;

    potatoPlayerGlove.visible = player.gloveIndex === potatoGloveIndex;

    const bots = [];
    const botColors = [
      0xff754a, 0xb77bff, 0xffd24a, 0x38d6a2, 0xff5d9e,
      0x75a7ff, 0xd5e85f, 0xff995d, 0x62d9e8, 0xe58cff
    ];

    const botNamePool = [
      'Bonkster', 'Bumble', 'Captain Chaos', 'Dizzy', 'Fumble',
      'Jellybean', 'Noodle', 'Pancake', 'Wobble', 'Zippy',
      'Sparky', 'Mango', 'Pebble', 'Biscuit', 'Turbo',
      'Twinkle', 'Crackle', 'Orbit', 'Velvet', 'Pip',
      'Rascal', 'Flare', 'Gizmo', 'Blip', 'Nugget',
      'Tater', 'Quill', 'Rumble', 'Kettle', 'Pixel'
    ];

    function shuffle(array) {
      for (let i = array.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [array[i], array[j]] = [array[j], array[i]];
      }
      return array;
    }

    function makeFighter(name, color, x, z, islandTraveler = false) {
      const root = new THREE.Group();
      const material = new THREE.MeshStandardMaterial({ color, roughness: 0.72 });
      const dark = new THREE.MeshStandardMaterial({ color: 0x253047, roughness: 0.85 });

      function part(geometry, mat, px, py, pz) {
        const mesh = new THREE.Mesh(geometry, mat);
        mesh.position.set(px, py, pz);
        mesh.castShadow = true;
        mesh.receiveShadow = true;
        root.add(mesh);
        return mesh;
      }

      part(new THREE.BoxGeometry(0.75, 0.8, 0.42), material, 0, 0, 0);
      part(new THREE.SphereGeometry(0.28, 16, 12), material, 0, 0.62, 0);
      const leftArm = part(new THREE.BoxGeometry(0.22, 0.66, 0.24), material, -0.53, -0.03, 0);
      const rightArm = part(new THREE.BoxGeometry(0.22, 0.66, 0.24), material, 0.53, -0.03, 0);
      const leftLeg = part(new THREE.BoxGeometry(0.27, 0.62, 0.29), dark, -0.2, -0.69, 0);
      const rightLeg = part(new THREE.BoxGeometry(0.27, 0.62, 0.29), dark, 0.2, -0.69, 0);

      const eyeMaterial = new THREE.MeshBasicMaterial({ color: 0x152033 });
      part(new THREE.SphereGeometry(0.035, 8, 8), eyeMaterial, -0.095, 0.67, -0.24);
      part(new THREE.SphereGeometry(0.035, 8, 8), eyeMaterial, 0.095, 0.67, -0.24);

      const gloveIndex = Math.random() < 1 / 150
        ? potatoGloveIndex
        : Math.floor(Math.random() * regularGlovesCount);
      const botGlove = makeGloveModel(gloves[gloveIndex].color, 0.65);
      botGlove.position.set(0.65, -0.12, -0.18);
      root.add(botGlove);

      root.position.set(x, floorY, z);
      scene.add(root);

      return {
        id: name.toLowerCase().replaceAll(' ', '-'),
        name,
        pos: root.position,
        vel: new THREE.Vector3(),
        root,
        leftArm,
        rightArm,
        leftLeg,
        rightLeg,
        grounded: true,
        ragdoll: 0,
        ragAngle: 0,
        ragdollSpin: new THREE.Vector3(),
        lastHitBy: null,
        kills: 0,
        isPlayer: false,
        gloveIndex,
        abilityCooldown: Math.random() * 2,
        shieldTime: 0,
        speedTime: 0,
        dashTime: 0,
        freezeTime: 0,
        fallingOut: false,
        fallTimer: 0,
        hitContacts: new Set(),
        phase: Math.random() * Math.PI * 2,
        islandTraveler,
        islandTripCooldown: 12 + Math.random() * 18,
        islandTrip: null,
        islandTripIsland: null,
        islandWaypoint: 0,
        islandStayTime: 0,
        reactionTargetId: null,
        reactionTime: 0,
        attackCooldown: Math.random() * 0.8,
        potatoBombArmed: false
      };
    }

    const shuffledBotNames = shuffle([...botNamePool]).slice(0, 10);

    for (let i = 0; i < 10; i++) {
      const angle = i * Math.PI * 2 / 10;
      const radius = 9 + (i % 3) * 1.1;
      const botName = shuffledBotNames[i] || `Bot ${i + 1}`;

      bots.push(makeFighter(
        botName,
        botColors[i],
        Math.cos(angle) * radius,
        Math.sin(angle) * radius,
        i % 3 === 0
      ));
    }

    const keys = new Set();
    const forward = new THREE.Vector3();
    const right = new THREE.Vector3();
    const moveDir = new THREE.Vector3();
    const playerMotionSamples = [];
    const abilityEffects = [];
    const potatoBombs = [];

    let yaw = 0;
    let pitch = 0;
    let slapAnimation = 0;
    let playerKnockoffs = 0;
    let noticeTimer = 0;
    let sampleClock = 0;
    let playerAttackSamples = 0;
    let playerSlaps = initialSlaps;

    let adminUnlocked = false;
    let lastNonAdminGloveIndex = savedGloveIndex;
    let timeStopRemaining = 0;
    let timeStopCooldown = 0;
    let kineticCooldown = 0;
    const timeStopHits = new Map();
    const kineticWaves = [];

    const codePanel = document.getElementById('codePanel');
    const codeInput = document.getElementById('codeInput');

    function playerForward() {
      return new THREE.Vector3(-Math.sin(yaw), 0, -Math.cos(yaw));
    }

    function showNotice(text) {
      document.getElementById('notice').textContent = text;
      noticeTimer = 1.4;
    }

    function updateSlapCounter() {
      document.getElementById('slapCounter').textContent = `Slaps: ${playerSlaps}`;
    }

    function updateTotalKills() {
      document.getElementById('killCounter').textContent =
        `Total kills: ${totalPlayerKills}`;
    }

    function saveGame() {
      try {
        localStorage.setItem(SAVE_KEY, JSON.stringify({
          slaps: playerSlaps,
          totalKills: totalPlayerKills,
          ownedGloves: [...ownedGloves],
          gloveIndex: lastNonAdminGloveIndex
        }));
      } catch {
        // Ignore storage failures silently.
      }
    }

    function unlockAffordableGloves() {
      const newlyUnlocked = [];

      for (const index of gloveUnlockOrder) {
        if (!ownedGloves.has(index) && playerSlaps >= gloves[index].cost) {
          ownedGloves.add(index);
          newlyUnlocked.push(gloves[index].name);
        }
      }

      if (newlyUnlocked.length > 0) {
        updateGloveStandAppearance();
        saveGame();
      }

      return newlyUnlocked;
    }

function equipGlove(index) {
  player.gloveIndex = index;
  playerGlove.visible = index !== potatoGloveIndex;
  potatoPlayerGlove.visible = index === potatoGloveIndex;

  if (index !== potatoGloveIndex) {
    playerGlove.traverse(obj => {
      if (obj.isMesh) obj.material.color.setHex(gloves[index].color);
    });
  }

  if (index !== adminGloveIndex) {
    lastNonAdminGloveIndex = index;
    saveGame();
  }
}


    function makePotatoBombVisual() {
      const potato = new THREE.Group();

      const body = new THREE.Mesh(
        new THREE.SphereGeometry(0.22, 16, 12),
        new THREE.MeshStandardMaterial({ color: 0xb77b45, roughness: 0.95 })
      );
      body.scale.set(1.15, 0.8, 1.3);
      potato.add(body);

      const spotsMaterial = new THREE.MeshStandardMaterial({ color: 0x573719 });
      for (const [x, y, z] of [[-0.1, 0.05, -0.18], [0.1, -0.05, -0.2]]) {
        const spot = new THREE.Mesh(
          new THREE.SphereGeometry(0.025, 8, 6),
          spotsMaterial
        );
        spot.position.set(x, y, z);
        potato.add(spot);
      }

      const canvas = document.createElement('canvas');
      canvas.width = 256;
      canvas.height = 128;
      const context = canvas.getContext('2d');
      const texture = new THREE.CanvasTexture(canvas);

      const label = new THREE.Sprite(
        new THREE.SpriteMaterial({ map: texture, transparent: true, depthTest: false })
      );
      label.scale.set(1.15, 0.58, 1);
      label.position.y = 0.55;
      potato.add(label);

      function setCountdown(seconds) {
        context.clearRect(0, 0, canvas.width, canvas.height);
        context.fillStyle = '#101828e8';
        context.fillRect(12, 16, 232, 96);
        context.strokeStyle = '#ffd166';
        context.lineWidth = 6;
        context.strokeRect(12, 16, 232, 96);
        context.fillStyle = '#ffffff';
        context.font = 'bold 68px system-ui';
        context.textAlign = 'center';
        context.textBaseline = 'middle';
        context.fillText(String(seconds), 128, 66);
        texture.needsUpdate = true;
      }

      setCountdown(10);
      return { potato, label, texture, setCountdown };
    }

    function transferPotatoBomb(attacker, target) {
      if (attacker.potatoBombArmed) {
        attacker.potatoBombArmed = false;
        const bomb = {
          carrier: target,
          creditedBy: attacker,
          remaining: 10,
          shownSeconds: 10,
          ...makePotatoBombVisual()
        };
        bomb.potato.position.set(target.pos.x, target.pos.y + 1.8, target.pos.z);
        scene.add(bomb.potato);
        potatoBombs.push(bomb);
        if (attacker.isPlayer) {
          showNotice('Potato Bomb armed! It is now orbiting the target.');
        }
        return;
      }

      const existing = potatoBombs.find(bomb => bomb.carrier === attacker);
      if (existing) {
        existing.carrier = target;
        existing.creditedBy = attacker;
      }
    }

    function updatePotatoBombs(dt) {
      for (let i = potatoBombs.length - 1; i >= 0; i--) {
        const bomb = potatoBombs[i];
        bomb.remaining -= dt;

        if (bomb.remaining <= 0) {
          const victim = bomb.carrier;
          const credit = bomb.creditedBy;

          scene.remove(bomb.potato);
          if (bomb.texture) bomb.texture.dispose();
          if (bomb.label && bomb.label.material && bomb.label.material.map) {
            bomb.label.material.map.dispose();
          }
          if (bomb.label && bomb.label.material) bomb.label.material.dispose();
          bomb.potato.traverse(obj => {
            if (obj.isMesh) {
              obj.geometry.dispose();
              if (obj.material) obj.material.dispose();
            }
          });

          potatoBombs.splice(i, 1);

          if (victim && !victim.fallingOut) {
            victim.lastHitBy = credit?.id ?? null;
            victim.fallingOut = true;
            victim.fallTimer = 0.05;
            victim.vel.set(0, 0, 0);

            if (victim.isPlayer) {
              showNotice('The potato bomb exploded!');
            } else if (credit && credit.isPlayer) {
              showNotice(`${victim.name} was potato-bombed!`);
            }
          }
          continue;
        }

        const seconds = Math.ceil(bomb.remaining);
        if (seconds !== bomb.shownSeconds) {
          bomb.shownSeconds = seconds;
          bomb.setCountdown(seconds);
        }

        const orbit = performance.now() * 0.004 + i * 1.7;
        bomb.potato.position.set(
          bomb.carrier.pos.x + Math.cos(orbit) * 0.9,
          bomb.carrier.pos.y + 1.9 + Math.sin(orbit * 1.4) * 0.15,
          bomb.carrier.pos.z + Math.sin(orbit) * 0.9
        );
      }
    }

    function showAbilityRing(position, color, radius = 5) {
      const mesh = new THREE.Mesh(
        new THREE.TorusGeometry(1, 0.06, 8, 32),
        new THREE.MeshBasicMaterial({
          color,
          transparent: true,
          opacity: 0.85
        })
      );
      mesh.rotation.x = Math.PI / 2;
      mesh.position.set(position.x, position.y + 0.12, position.z);
      mesh.scale.setScalar(0.1);
      scene.add(mesh);
      abilityEffects.push({ mesh, age: 0, duration: 0.55, radius });
    }

    function startGame() {
      document.getElementById('start').style.display = 'none';
      renderer.domElement.requestPointerLock?.();
    }

    function isLookingAtPotatoButton() {
      const raycaster = new THREE.Raycaster();
      raycaster.setFromCamera(new THREE.Vector2(0, 0), camera);
      return raycaster.intersectObject(potatoRevealButton).length > 0;
    }

    function openCodePanel() {
      codePanel.hidden = false;
      keys.clear();
      document.getElementById('start').style.display = 'none';
      document.exitPointerLock?.();
      setTimeout(() => codeInput.focus(), 0);
    }

    function closeCodePanel() {
      codePanel.hidden = true;
      document.getElementById('start').style.display = 'none';
      renderer.domElement.requestPointerLock?.();
    }

    function submitCode() {
      const code = codeInput.value.trim().toLowerCase();

      if (code === 'potato') {
        ownedGloves.add(potatoGloveIndex);
        saveGame();
        showNotice('Congrats! Potato glove unlocked!');
      } else if (code === 'dogsuperfast') {
        adminUnlocked = true;
        equipGlove(adminGloveIndex);
        showNotice(
          'Welcome admin please try out our new prototype it is incredibly powerful too.'
        );
      } else {
        showNotice('Invalid code.');
        return;
      }

      codeInput.value = '';
      codePanel.hidden = true;
      renderer.domElement.requestPointerLock?.();
    }

    document.getElementById('start').addEventListener('click', startGame);
    document.getElementById('closeCode').addEventListener('click', closeCodePanel);
    document.getElementById('submitCode').addEventListener('click', submitCode);

    codeInput.addEventListener('keydown', event => {
      if (event.key === 'Enter') submitCode();
    });

    renderer.domElement.addEventListener('click', () => {
      if (document.pointerLockElement !== renderer.domElement) {
        renderer.domElement.requestPointerLock?.();
        return;
      }

      if (player.inLobby && isLookingAtPotatoButton()) {
        potatoStand.visible = true;
        showNotice('A new glove appeared in the lobby!');
        return;
      }

      if (player.inLobby && trySelectGlove()) return;
      slap(player, playerForward());
    });

    document.addEventListener('pointerlockchange', () => {
      if (!codePanel.hidden) {
        document.getElementById('start').style.display = 'none';
        return;
      }

      document.getElementById('start').style.display =
        document.pointerLockElement === renderer.domElement ? 'none' : 'grid';
    });

    document.addEventListener('mousemove', event => {
      if (document.pointerLockElement !== renderer.domElement || !codePanel.hidden) return;
      yaw -= event.movementX * 0.0022;
      pitch -= event.movementY * 0.002;
      pitch = THREE.MathUtils.clamp(pitch, -1.15, 1.15);
      camera.rotation.order = 'YXZ';
      camera.rotation.set(pitch, yaw, 0);
    });

    const movementKeys = new Set([
      'KeyW', 'KeyA', 'KeyS', 'KeyD',
      'ArrowUp', 'ArrowDown', 'ArrowLeft', 'ArrowRight'
    ]);

    document.addEventListener('keydown', event => {
      if (!codePanel.hidden) {
        if (event.key === 'Escape') {
          closeCodePanel();
        }
        return;
      }

      if (
        event.code === 'KeyC' &&
        !event.repeat &&
        !event.target.matches('input, textarea')
      ) {
        event.preventDefault();
        openCodePanel();
        return;
      }

      if (
        movementKeys.has(event.code) ||
        event.code === 'Space' ||
        event.code === 'KeyT' ||
        event.code === 'KeyK'
      ) {
        event.preventDefault();
      }

      keys.add(event.code);

      if (event.code === 'Space' && !event.repeat) jump(player);
      if (event.code === 'KeyT' && !event.repeat) activateTimeStop();
      if (event.code === 'KeyK' && !event.repeat) activateKineticOverload();

      if (
        event.code === 'KeyE' &&
        !event.repeat &&
        player.gloveIndex !== adminGloveIndex
      ) {
        useAbility(player);
      }
    });

    document.addEventListener('keyup', event => keys.delete(event.code));
    document.addEventListener('contextmenu', event => event.preventDefault());

    function trySelectGlove() {
      const look = playerForward();

      if (potatoStand.visible) {
        const dx = potatoStand.position.x - player.pos.x;
        const dz = potatoStand.position.z - player.pos.z;
        const distance = Math.hypot(dx, dz);

        if (distance < 10 && distance > 0.1) {
          const dot = (dx * look.x + dz * look.z) / distance;

          if (dot > 0.88) {
            if (ownedGloves.has(potatoGloveIndex)) {
              equipGlove(potatoGloveIndex);
              showNotice('Potato glove equipped!');
            } else {
              showNotice('maybe a code might help.');
            }
            return true;
          }
        }
      }

      let selected = null;
      let bestDot = 0.88;

      for (const stand of gloveStands) {
        const dx = stand.x - player.pos.x;
        const dz = stand.z - player.pos.z;
        const distance = Math.hypot(dx, dz);
        if (distance > 10 || distance < 0.1) continue;

        const dot = (dx * look.x + dz * look.z) / distance;
        if (dot > bestDot) {
          bestDot = dot;
          selected = stand;
        }
      }

      if (!selected) return false;

      const glove = gloves[selected.index];
      const nextGloveIndex = getNextGloveToUnlock();

      if (!ownedGloves.has(selected.index)) {
        if (selected.index !== nextGloveIndex) {
          const nextGlove = gloves[nextGloveIndex];
          showNotice(`Unlock nextGlove.namefirst({nextGlove.cost} slaps).`);
          return true;
        }

        if (playerSlaps < glove.cost) {
          showNotice(`${glove.name} requires ${glove.cost} slaps. You have ${playerSlaps}.`);
          return true;
        }

        ownedGloves.add(selected.index);
        updateGloveStandAppearance();
        saveGame();
        showNotice(`${glove.name} unlocked! Your slaps were not spent.`);
      }

      equipGlove(selected.index);
      showNotice(`${gloves[player.gloveIndex].name} glove equipped!`);
      return true;
    }

    function jump(entity) {
      if (entity.grounded && entity.ragdoll <= 0 && !entity.fallingOut) {
        entity.vel.y = entity.isPlayer ? 8.2 : 7.2 + Math.random() * 1.2;
        entity.grounded = false;
      }
    }

    function applyKnockback(target, direction, strength = 8.2, lift = 3.2) {
      if (target.shieldTime > 0) {
        target.shieldTime = 0;
        if (target.isPlayer) showNotice('Your Guard blocked the hit!');
        return false;
      }

      strength *= 3;
      lift *= 3;

      target.vel.x += direction.x * strength;
      target.vel.z += direction.z * strength;
      target.vel.y = Math.max(target.vel.y, lift);
      target.grounded = false;
      target.ragdoll = 1.15;
      target.ragAngle = (Math.random() < 0.5 ? -1 : 1) * (0.7 + Math.random() * 0.6);

      if (!target.isPlayer) {
        target.ragdollSpin.set(
          (Math.random() - 0.5) * 8,
          (Math.random() - 0.5) * 8,
          (Math.random() - 0.5) * 8
        );
      }

      return true;
    }

    function applyAbilityKnockback(target, direction, strength = 8.2, lift = 3.2) {
      return applyKnockback(target, direction, strength * 0.25, lift * 0.25);
    }
   function queueTimeStopHit(target, direction, attacker = player) {
      const hit = timeStopHits.get(target) || {
        count: 0,
        x: 0,
        z: 0,
        attacker
      };

      hit.count++;
      hit.x += direction.x;
      hit.z += direction.z;
      hit.attacker = attacker;
      timeStopHits.set(target, hit);
    }

    function hitWithAdminPower(target, direction) {
      if (timeStopRemaining > 0) {
        queueTimeStopHit(target, direction, player);
        return;
      }

      if (applyKnockback(target, direction)) {
        target.lastHitBy = player.id;
      }
    }

    function endTimeStop() {
      timeStopRemaining = 0;
      renderer.domElement.style.filter = '';

      for (const [target, hit] of timeStopHits) {
        if (!target || target.fallingOut) continue;

        const direction = new THREE.Vector3(hit.x, 0, hit.z);
        if (direction.lengthSq() < 0.001) direction.copy(playerForward());
        direction.normalize();

        if (applyKnockback(target, direction, 8.2 * hit.count, 3.2)) {
          target.lastHitBy = hit.attacker.id;
        }
      }

      timeStopHits.clear();
    }

    function activateTimeStop() {
      if (
        !adminUnlocked ||
        player.gloveIndex !== adminGloveIndex ||
        timeStopCooldown > 0 ||
        timeStopRemaining > 0
      ) return;

      timeStopCooldown = 10;
      timeStopRemaining = 5;
      renderer.domElement.style.filter = 'grayscale(0.7)';
      showNotice('TIME STOP!');
    }

    function activateKineticOverload() {
      if (
        !adminUnlocked ||
        player.gloveIndex !== adminGloveIndex ||
        kineticCooldown > 0
      ) return;

      kineticCooldown = 10;

      const ball = new THREE.Mesh(
        new THREE.SphereGeometry(1, 32, 24),
        new THREE.MeshBasicMaterial({
          color: 0x9b35ff,
          transparent: true,
          opacity: 0.28,
          depthWrite: false,
          side: THREE.DoubleSide
        })
      );

      const center = player.pos.clone();
      center.y += 0.8;
      ball.position.copy(center);
      ball.scale.setScalar(0);
      scene.add(ball);

      kineticWaves.push({
        ball,
        center,
        age: 0,
        hitTargets: new Set(),
        maxRadius: satelliteDistance + satelliteRadius
      });

      showNotice('KINETIC OVERLOAD!');
    }

    function updateKineticWaves(dt) {
      for (let i = kineticWaves.length - 1; i >= 0; i--) {
        const wave = kineticWaves[i];
        wave.age += dt;

        const expansion = Math.min(wave.age / 5, 1);
        const pulse = 1 + Math.sin(wave.age * 8) * 0.035;
        const radius = wave.maxRadius * expansion * pulse;

        wave.ball.scale.setScalar(radius);
        wave.ball.material.opacity =
          wave.age <= 5
            ? 0.28 * (0.85 + 0.15 * Math.sin(wave.age * 8))
            : 0.28 * Math.max(0, 1 - (wave.age - 5) / 5);

        for (const target of bots) {
          if (wave.hitTargets.has(target) || target.fallingOut) continue;

          if (getSatelliteIslandIndexAt(target.pos.x, target.pos.z) !== -1) continue;

          if (target.pos.distanceTo(wave.center) <= radius) {
            wave.hitTargets.add(target);

            const direction = target.pos.clone().sub(wave.center);
            direction.y = 0;
            if (direction.lengthSq() < 0.001) direction.copy(playerForward());
            direction.normalize();

            hitWithAdminPower(target, direction);
          }
        }

        if (wave.age >= 10) {
          scene.remove(wave.ball);
          wave.ball.geometry.dispose();
          wave.ball.material.dispose();
          kineticWaves.splice(i, 1);
        }
      }
    }

    function slap(attacker, direction) {
      if (attacker.inLobby || attacker.ragdoll > 0 || attacker.fallingOut) return;

      if (attacker.isPlayer) {
        slapAnimation = 0.24;
        playerAttackSamples++;
      }

      let best = null;
      let bestDistance = Infinity;

      for (const target of [player, ...bots]) {
        if (
          target === attacker ||
          (target.ragdoll > 0.45 &&
            !(timeStopRemaining > 0 && attacker.isPlayer)) ||
          target.fallingOut
        ) continue;

        const dx = target.pos.x - attacker.pos.x;
        const dz = target.pos.z - attacker.pos.z;
        const distance = Math.hypot(dx, dz);

        const hitRange = attacker.isPlayer
          ? 4.0
          : target.isPlayer
            ? 3.15
            : 3.55;

        if (distance > hitRange || distance < 0.01) continue;

        const isBotSlappingPlayer = !attacker.isPlayer && target.isPlayer;

        if (
          isBotSlappingPlayer &&
          Math.abs(target.pos.y - attacker.pos.y) > 0.95
        ) {
          continue;
        }

        const facing = (dx * direction.x + dz * direction.z) / distance;
        const requiredFacing = isBotSlappingPlayer ? 0.78 : 0.28;

        if (facing > requiredFacing && distance < bestDistance) {
          best = target;
          bestDistance = distance;
        }
      }

      if (!best) return;

      const bombCarrierTransfer =
        attacker.potatoBombArmed ||
        potatoBombs.some(bomb => bomb.carrier === attacker);

      if (bombCarrierTransfer) {
        transferPotatoBomb(attacker, best);

        if (attacker.isPlayer && !best.isPlayer) {
          playerSlaps++;
          updateSlapCounter();
          const unlockedGloves = unlockAffordableGloves();
          saveGame();

          if (unlockedGloves.length) {
            const unlockText =
              ` Glove${unlockedGloves.length > 1 ? 's' : ''} unlocked: ${unlockedGloves.join(', ')}!`;
            showNotice(`${best.name} got the potato bomb!${unlockText}`);
          } else {
            showNotice(`${best.name} got the potato bomb!`);
          }
        }

        if (attacker.isPlayer && best.isPlayer) {
          showNotice(`${best.name} got the potato bomb!`);
        }
        return;
      }

      if (timeStopRemaining > 0 && attacker.isPlayer) {
        const directionToTarget = new THREE.Vector3(
          best.pos.x - attacker.pos.x,
          0,
          best.pos.z - attacker.pos.z
        );

        if (directionToTarget.lengthSq() < 0.001) {
          directionToTarget.copy(direction);
        }
        directionToTarget.normalize();

        queueTimeStopHit(best, directionToTarget, attacker);
        best.lastHitBy = attacker.id;

        if (!best.isPlayer) {
          playerSlaps++;
          updateSlapCounter();
          unlockAffordableGloves();
          saveGame();
        }
        return;
      }

      const push = new THREE.Vector3(
        best.pos.x - attacker.pos.x,
        0,
        best.pos.z - attacker.pos.z
      );
      if (push.lengthSq() < 0.001) push.copy(direction);
      push.normalize();

      const botOnSmallIsland =
        !attacker.isPlayer &&
        getSatelliteIslandIndexAt(attacker.pos.x, attacker.pos.z) !== -1;

      const slapStrength = botOnSmallIsland
        ? 2.05
        : attacker.isPlayer
          ? 8.2
          : 4.1;

      if (applyKnockback(best, push, slapStrength, 3.2)) {
        best.lastHitBy = attacker.id;

        if (attacker.isPlayer && !best.isPlayer) {
          playerSlaps++;
          updateSlapCounter();
          const unlockedGloves = unlockAffordableGloves();
          saveGame();

          if (unlockedGloves.length) {
            const unlockText =
              ` Glove${unlockedGloves.length > 1 ? 's' : ''} unlocked: ${unlockedGloves.join(', ')}!`;
            showNotice(`${best.name} got slapped!${unlockText}`);
          } else {
            showNotice(`${best.name} got slapped!`);
          }
        }

        if (attacker.isPlayer && best.isPlayer) {
          showNotice(`${best.name} got slapped!`);
        }
      }
    }

    function useAbility(entity) {
      if (
        entity.inLobby || entity.ragdoll > 0 ||
        entity.fallingOut || entity.abilityCooldown > 0
      ) return;

      const glove = gloves[entity.gloveIndex];
      const facing = entity.isPlayer
        ? playerForward()
        : new THREE.Vector3(
            -Math.sin(entity.root.rotation.y),
            0,
            -Math.cos(entity.root.rotation.y)
          );

      entity.abilityCooldown =
        glove.ability === 'Potato Bomb'
          ? 30
          : entity.isPlayer
            ? 3.5
            : 4.5;

      const targets = bots.filter(
        bot => bot !== entity && bot.ragdoll <= 0.4 && !bot.fallingOut
      );
      if (entity !== player && !player.inLobby && !player.fallingOut) {
        targets.push(player);
      }

      const nearest = targets
        .map(target => ({ target, distance: target.pos.distanceTo(entity.pos) }))
        .filter(item => item.distance < 10)
        .sort((a, b) => a.distance - b.distance)[0]?.target;

      const nearby = targets.filter(target => target.pos.distanceTo(entity.pos) < 7);
      const color = glove.color;

      switch (glove.ability) {
        case 'Rocket Dash': {
          const dashDistance = getIslandRadiusAt(entity.pos.x, entity.pos.z);
          const dashDuration = 0.45;

          entity.dashTime = dashDuration;
          entity.vel.x = facing.x * (dashDistance / dashDuration);
          entity.vel.z = facing.z * (dashDistance / dashDuration);
          entity.vel.y = Math.max(entity.vel.y, 2);
          showAbilityRing(entity.pos, color, 3);
          break;
        }

        case 'Thunderclap':
          showAbilityRing(entity.pos, color, 7);
          for (const target of nearby) {
            const direction = target.pos.clone().sub(entity.pos);
            direction.y = 0;
            direction.normalize();
            if (applyAbilityKnockback(target, direction, 10, 4)) {
              target.lastHitBy = entity.id;
            }
          }
          break;

        case 'Sky Pop':
          entity.vel.y = 12;
          entity.grounded = false;
          showAbilityRing(entity.pos, color, 4);
          break;

        case 'Magnetic Pull':
          showAbilityRing(entity.pos, color, 6);
          for (const target of nearby) {
            const direction = entity.pos.clone().sub(target.pos);
            direction.y = 0;
            direction.normalize();
            target.vel.x += direction.x * 2;
            target.vel.z += direction.z * 2;
            target.lastHitBy = entity.id;
          }
          break;

        case 'Freeze':
          if (nearest) {
            nearest.freezeTime = 2;
            nearest.vel.set(0, 0, 0);
            showAbilityRing(nearest.pos, color, 2.5);
            if (entity.isPlayer) showNotice(`${nearest.name} frozen!`);
          } else if (entity.isPlayer) {
            showNotice('No target nearby to freeze!');
          }
          break;

        case 'Blink Forward':
          entity.pos.x += facing.x * 5;
          entity.pos.z += facing.z * 5;
          if (!entity.isPlayer) break;

          const blinkRadius = Math.hypot(entity.pos.x, entity.pos.z);
          if (!entity.inLobby && blinkRadius > 21) {
            entity.pos.x *= 21 / blinkRadius;
            entity.pos.z *= 21 / blinkRadius;
          }
          showAbilityRing(entity.pos, color, 3);
          break;

        case 'Glove Guard':
          entity.shieldTime = 2.5;
          showAbilityRing(entity.pos, color, 3);
          break;

        case 'Ground Quake':
          showAbilityRing(entity.pos, color, 8);
          for (const target of nearby) {
            const direction = target.pos.clone().sub(entity.pos);
            direction.y = 0;
            direction.normalize();
            if (applyAbilityKnockback(target, direction, 11, 6)) {
              target.lastHitBy = entity.id;
            }
          }
          break;

        case 'Super Speed':
          entity.speedTime = 4;
          showAbilityRing(entity.pos, color, 3);
          break;

        case 'Launch Target':
          if (nearest) {
            const direction = nearest.pos.clone().sub(entity.pos);
            direction.y = 0;
            direction.normalize();
            if (applyAbilityKnockback(nearest, direction, 5, 13)) {
              nearest.lastHitBy = entity.id;
            }
            showAbilityRing(nearest.pos, color, 3);
          } else if (entity.isPlayer) {
            showNotice('No target nearby to launch!');
          }
          break;

        case 'Potato Bomb':
          entity.potatoBombArmed = true;
          if (entity.isPlayer) {
            showNotice('Potato Bomb armed! Your next slap plants a bomb.');
          }
          break;
      }

      if (entity.isPlayer) showNotice(`${glove.ability}!`);
    }

    function nearestTarget(bot) {
      const candidates = bots.filter(
        other => other !== bot && other.ragdoll <= 0.4 && !other.fallingOut
      );
      if (!player.inLobby && !player.fallingOut) candidates.push(player);

      let target = null;
      let bestDistance = Infinity;
      for (const candidate of candidates) {
        const distance = bot.pos.distanceTo(candidate.pos);
        if (distance < bestDistance) {
          target = candidate;
          bestDistance = distance;
        }
      }
      return { target, distance: bestDistance };
    }

    function botThink(bot, dt) {
      if (
        bot.ragdoll > 0 ||
        bot.freezeTime > 0 ||
        bot.fallingOut ||
        bot.dashTime > 0
      ) return;

      bot.attackCooldown = Math.max(0, bot.attackCooldown - dt);
      bot.reactionTime = Math.max(0, bot.reactionTime - dt);
      bot.islandTripCooldown = Math.max(0, bot.islandTripCooldown - dt);

      const { target, distance } = nearestTarget(bot);
      if (!target) return;

      if (bot.reactionTargetId !== target.id) {
        bot.reactionTargetId = target.id;
        bot.reactionTime = 0.45;
      }

      if (
        bot.islandTraveler &&
        bot.islandTripIsland === null &&
        bot.islandTripCooldown <= 0 &&
        distance > 12
      ) {
        const availableIslands = satelliteIslands
          .map((island, index) => ({ island, index }))
          .filter(({ island, index }) => {
            const botsOnIsland = bots.filter(other => {
              if (other === bot || other.fallingOut) return false;
              const reserved = other.islandTripIsland === index;
              const standingThere =
                Math.hypot(other.pos.x - island.x, other.pos.z - island.z) <=
                island.radius;
              return reserved || standingThere;
            }).length;

            return botsOnIsland < 2;
          });

        if (availableIslands.length > 0) {
          const { island, index } =
            availableIslands[Math.floor(Math.random() * availableIslands.length)];

          const direction = new THREE.Vector2(island.x, island.z).normalize();
          const perpendicular = new THREE.Vector2(-direction.y, direction.x);
          const bridgeOffset = (Math.random() < 0.5 ? -1 : 1) * 1.6;

          bot.islandTripIsland = index;
          bot.islandWaypoint = 0;
          bot.islandTrip = [
            new THREE.Vector3(
              direction.x * (arenaRadius - 2) + perpendicular.x * bridgeOffset,
              floorY,
              direction.y * (arenaRadius - 2) + perpendicular.y * bridgeOffset
            ),
            new THREE.Vector3(
              direction.x * (satelliteDistance - island.radius + 1) +
                perpendicular.x * bridgeOffset,
              floorY,
              direction.y * (satelliteDistance - island.radius + 1) +
                perpendicular.y * bridgeOffset
            ),
            new THREE.Vector3(
              island.x - direction.x * island.radius * 0.35,
              floorY,
              island.z - direction.y * island.radius * 0.35
            )
          ];
        } else {
          bot.islandTripCooldown = 4;
        }
      }

      if (bot.islandTrip) {
        while (
          bot.islandWaypoint < bot.islandTrip.length &&
          Math.hypot(
            bot.islandTrip[bot.islandWaypoint].x - bot.pos.x,
            bot.islandTrip[bot.islandWaypoint].z - bot.pos.z
          ) < 2.2
        ) {
          bot.islandWaypoint++;
        }

        if (bot.islandWaypoint >= bot.islandTrip.length) {
          bot.islandTrip = null;
          bot.islandWaypoint = 0;
          bot.islandStayTime = 12 + Math.random() * 8;
        }
      } else if (bot.islandStayTime > 0) {
        bot.islandStayTime = Math.max(0, bot.islandStayTime - dt);

        if (bot.islandStayTime === 0) {
          bot.islandTripIsland = null;
          bot.islandTripCooldown = 18 + Math.random() * 15;
        }
      }

      const toTarget = new THREE.Vector3(
        target.pos.x - bot.pos.x,
        0,
        target.pos.z - bot.pos.z
      ).normalize();

      const playerBias = playerMotionSamples.length
        ? playerMotionSamples.reduce((sum, n) => sum + n, 0) / playerMotionSamples.length
        : 0;
      const attacksOften = playerAttackSamples > 1;
      const side = new THREE.Vector3(-toTarget.z, 0, toTarget.x);
      const desired = toTarget.clone();

      if (bot.islandTrip) {
        const waypoint = bot.islandTrip[bot.islandWaypoint];
        desired.set(
          waypoint.x - bot.pos.x,
          0,
          waypoint.z - bot.pos.z
        ).normalize();
      } else if (bot.islandStayTime > 0) {
        desired.set(0, 0, 0);
      } else if (target.isPlayer && distance < 7 && Math.abs(playerBias) > 0.12) {
        desired.addScaledVector(
          side,
          -Math.sign(playerBias) * (attacksOften ? 0.65 : 0.35)
        );
      } else if (distance < 3.8) {
        desired.addScaledVector(toTarget, -0.65);
        desired.addScaledVector(side, Math.sin(bot.phase) * 0.35);
      }

      desired.normalize();

      const reactionScale = bot.reactionTime > 0 ? 0.55 : 1;
      const speed = bot.speedTime > 0 ? 6.5 : 6.1;

      bot.vel.x += (desired.x * speed * reactionScale - bot.vel.x) * Math.min(1, dt * 3.5);
      bot.vel.z += (desired.z * speed * reactionScale - bot.vel.z) * Math.min(1, dt * 3.5);

      if (desired.lengthSq() > 0.001) {
        const facingDirection = bot.islandTrip ? desired : toTarget;
        bot.root.rotation.y = Math.atan2(-facingDirection.x, -facingDirection.z);
      }

      bot.phase += dt * (2 + bot.kills * 0.1);

      const distanceNow = bot.pos.distanceTo(target.pos);
      if (
        distanceNow < 3.1 &&
        !bot.hitContacts.has(target.id) &&
        bot.attackCooldown <= 0 &&
        bot.reactionTime <= 0
      ) {
        bot.hitContacts.add(target.id);
        slap(bot, toTarget);
        bot.attackCooldown = 0.8 + Math.random() * 0.5;
      }

      if (distanceNow > 3.7) bot.hitContacts.delete(target.id);

      if (bot.abilityCooldown <= 0 && distance < 8 && Math.random() < dt * 0.45) {
        useAbility(bot);
      }

      if (bot.grounded && distance > 4 && Math.random() < dt * 0.28) {
        jump(bot);
      }
    }

    function goToLobby() {
      player.inLobby = true;
      player.pos.set(lobbyCenter.x, floorY, 10);
      player.vel.set(0, 0, 0);
      player.grounded = true;
      player.ragdoll = 0;
      player.lastHitBy = null;
      player.fallingOut = false;
      player.fallTimer = 0;
      player.hitContacts.clear();
      player.potatoBombArmed = false;
      yaw = 0;
      showNotice('Lobby: walk around and click a glove stand to choose!');
    }

    function returnToArena() {
      player.inLobby = false;
      player.pos.set(0, floorY, 0);
      player.vel.set(0, 0, 0);
      player.grounded = true;
      player.ragdoll = 0;
      player.lastHitBy = null;
      player.fallingOut = false;
      player.fallTimer = 0;
      player.hitContacts.clear();
      player.potatoBombArmed = false;
      yaw = 0;
      showNotice('Back to the arena!');
    }

    function resetBot(bot) {
      const angle = Math.random() * Math.PI * 2;
      const radius = 6 + Math.random() * 9;
      bot.pos.set(Math.cos(angle) * radius, floorY, Math.sin(angle) * radius);
      bot.vel.set(0, 0, 0);
      bot.grounded = true;
      bot.ragdoll = 0;
      bot.lastHitBy = null;
      bot.hitContacts.clear();
      bot.root.rotation.set(0, 0, 0);
      bot.fallingOut = false;
      bot.fallTimer = 0;
      bot.islandTrip = null;
      bot.islandTripIsland = null;
      bot.islandWaypoint = 0;
      bot.islandStayTime = 0;
      bot.islandTripCooldown = 12 + Math.random() * 18;
      bot.reactionTargetId = null;
      bot.reactionTime = 0;
      bot.attackCooldown = 0.5;
      bot.potatoBombArmed = false;
    }

    function countFall(entity) {
      if (entity.lastHitBy) {
        const winner = [player, ...bots].find(
          fighter => fighter.id === entity.lastHitBy
        );
        if (winner) {
          winner.kills++;

          if (winner.isPlayer) {
            playerKnockoffs++;
            totalPlayerKills++;
            updateTotalKills();
            saveGame();

            document.getElementById('score').textContent =
              `Your knock-offs: ${playerKnockoffs}`;
            showNotice(`You knocked ${entity.name} off!`);
          }
        }
      } else if (entity.isPlayer) {
        showNotice('You fell off the island!');
      }
    }

    function updateFighter(entity, dt) {
      entity.ragdoll = Math.max(0, entity.ragdoll - dt);
      entity.abilityCooldown = Math.max(0, entity.abilityCooldown - dt);
      entity.shieldTime = Math.max(0, entity.shieldTime - dt);
      entity.speedTime = Math.max(0, entity.speedTime - dt);
      entity.dashTime = Math.max(0, entity.dashTime - dt);
      entity.freezeTime = Math.max(0, entity.freezeTime - dt);

      if (entity.isPlayer) {
        forward.copy(playerForward());
        right.set(Math.cos(yaw), 0, -Math.sin(yaw));
        moveDir.set(0, 0, 0);

        if (keys.has('KeyW') || keys.has('ArrowUp')) moveDir.add(forward);
        if (keys.has('KeyS') || keys.has('ArrowDown')) moveDir.sub(forward);
        if (keys.has('KeyD') || keys.has('ArrowRight')) moveDir.add(right);
        if (keys.has('KeyA') || keys.has('ArrowLeft')) moveDir.sub(right);

        if (entity.dashTime > 0) {
          // Preserve dash velocity.
        } else if (
          moveDir.lengthSq() > 0 &&
          entity.ragdoll <= 0 &&
          !entity.fallingOut
        ) {
          moveDir.normalize();
          const speed = entity.speedTime > 0 ? 10 : 7;
          entity.vel.x += (moveDir.x * speed - entity.vel.x) * Math.min(1, dt * 10);
          entity.vel.z += (moveDir.z * speed - entity.vel.z) * Math.min(1, dt * 10);
        } else if (entity.ragdoll <= 0 && !entity.fallingOut) {
          entity.vel.x *= Math.max(0, 1 - dt * 8);
          entity.vel.z *= Math.max(0, 1 - dt * 8);
        }

        if (entity.inLobby) {
          entity.pos.x += entity.vel.x * dt;
          entity.pos.z += entity.vel.z * dt;
          entity.vel.x *= Math.max(0, 1 - dt * 2.5);
          entity.vel.z *= Math.max(0, 1 - dt * 2.5);
          entity.pos.y = floorY;

          const dx = entity.pos.x - lobbyCenter.x;
          const dz = entity.pos.z - lobbyCenter.z;
          const distance = Math.hypot(dx, dz);
          if (distance > 14.5) {
            entity.pos.x = lobbyCenter.x + dx / distance * 14.5;
            entity.pos.z = lobbyCenter.z + dz / distance * 14.5;
          }

          if (Math.hypot(entity.pos.x - portalX, entity.pos.z - portalZ) < 2.2) {
            returnToArena();
          }
        }
      } else {
        botThink(entity, dt);
      }

      if (!entity.inLobby) {
        if (entity.fallingOut) {
          entity.vel.x = 0;
          entity.vel.z = 0;
          entity.vel.y -= 20 * dt;
          entity.pos.y += entity.vel.y * dt;
        } else if (entity.freezeTime > 0) {
          entity.vel.set(0, 0, 0);
        } else {
          entity.vel.y -= 20 * dt;
          entity.pos.addScaledVector(entity.vel, dt);

          if (entity.pos.y <= floorY) {
            entity.pos.y = floorY;
            if (entity.vel.y < 0) entity.vel.y = 0;
            entity.grounded = true;
          }
        }
      } else {
        entity.pos.y = floorY;
      }

      const outsideArena = !entity.inLobby && (
        !isOnArenaPlatform(entity.pos.x, entity.pos.z) ||
        entity.pos.y < floorY - 0.5
      );

      if (!entity.inLobby && !entity.fallingOut && outsideArena) {
        entity.fallingOut = true;
        entity.fallTimer = 2.2;
        entity.vel.x = 0;
        entity.vel.z = 0;
        entity.grounded = false;
        if (entity.isPlayer) showNotice('You fell off! Falling...');
      }

      if (entity.fallingOut) {
        entity.fallTimer -= dt;

        if (entity.fallTimer <= 0) {
          countFall(entity);
          if (entity.isPlayer) goToLobby();
          else resetBot(entity);
        }
      }

      if (!entity.isPlayer) {
        const walk = Math.sin(entity.phase) * (entity.grounded ? 0.42 : 0.12);
        entity.leftArm.rotation.x = walk;
        entity.rightArm.rotation.x = -walk;
        entity.leftLeg.rotation.x = -walk;
        entity.rightLeg.rotation.x = walk;

        if (entity.ragdoll > 0) {
          const flop =
            Math.sin(performance.now() * 0.025 + entity.phase) *
            entity.ragdoll *
            0.65;

          entity.root.rotation.x += entity.ragdollSpin.x * dt;
          entity.root.rotation.y += entity.ragdollSpin.y * dt;
          entity.root.rotation.z =
            entity.ragAngle * Math.min(1, entity.ragdoll * 2) + flop;

          entity.leftArm.rotation.z = -1.4 - flop;
          entity.rightArm.rotation.z = 1.4 + flop;
          entity.leftLeg.rotation.z = 0.8 + flop;
          entity.rightLeg.rotation.z = -0.8 - flop;
        } else {
          entity.root.rotation.x *= Math.max(0, 1 - dt * 8);
          entity.root.rotation.z *= Math.max(0, 1 - dt * 8);
          entity.leftArm.rotation.z = 0;
          entity.rightArm.rotation.z = 0;
          entity.leftLeg.rotation.z = 0;
          entity.rightLeg.rotation.z = 0;
        }
      }
    }

    function updateHUD() {
      const glove = gloves[player.gloveIndex];
      document.getElementById('where').textContent =
        player.inLobby ? 'Lobby' : 'Arena';
      document.getElementById('equipped').textContent = `Glove: ${glove.name}`;
      document.getElementById('ability').textContent =
        player.gloveIndex === adminGloveIndex
          ? `Time Stop (T): ${timeStopCooldown.toFixed(1)}s · Kinetic Overload (K): ${kineticCooldown.toFixed(1)}s`
          : `Ability: ${glove.ability} (E)` +
            (player.abilityCooldown > 0
              ? ` — ${player.abilityCooldown.toFixed(1)}s`
              : '');

      const rows = [player, ...bots]
        .sort((a, b) => b.kills - a.kills)
        .map((fighter, index) =>
          `<div><span>${index + 1}. ${fighter.name}</span><span>${fighter.kills}</span></div>`
        ).join('');
      document.getElementById('leaderboard').innerHTML =
        `<strong>Knock-offs</strong>${rows}`;
    }

    let last = performance.now();

    function animate(now) {
      requestAnimationFrame(animate);
      const dt = Math.min((now - last) / 1000, 0.04);
      last = now;

      updateFighter(player, dt);

      if (timeStopRemaining > 0) {
        timeStopRemaining = Math.max(0, timeStopRemaining - dt);
        if (timeStopRemaining === 0) endTimeStop();
      } else {
        for (const bot of bots) updateFighter(bot, dt);
        updatePotatoBombs(dt);
      }

      timeStopCooldown = Math.max(0, timeStopCooldown - dt);
      kineticCooldown = Math.max(0, kineticCooldown - dt);
      updateKineticWaves(dt);

      camera.position.set(player.pos.x, player.pos.y + 0.65, player.pos.z);

      const activeGlove =
        player.gloveIndex === potatoGloveIndex
          ? potatoPlayerGlove
          : playerGlove;

      if (slapAnimation > 0) {
        slapAnimation = Math.max(0, slapAnimation - dt);
        const swing = 1 - slapAnimation / 0.24;
        activeGlove.position.x = 0.48 + Math.sin(swing * Math.PI) * 0.28;
        activeGlove.position.z = -0.78 - Math.sin(swing * Math.PI) * 0.62;
        activeGlove.rotation.y = -Math.sin(swing * Math.PI) * 0.45;
      } else {
        activeGlove.position.set(0.48, -0.38, -0.78);
        activeGlove.rotation.set(0, 0, 0);
      }

      portal.rotation.z += dt * 0.55;
      portalCore.rotation.z -= dt * 0.3;
      buttonGlow.rotation.z -= dt * 0.7;

      for (let i = abilityEffects.length - 1; i >= 0; i--) {
        const effect = abilityEffects[i];
        effect.age += dt;

        const progress = Math.min(effect.age / effect.duration, 1);
        effect.mesh.scale.setScalar(0.1 + effect.radius * progress);
        effect.mesh.material.opacity = 0.85 * (1 - progress);

        if (progress >= 1) {
          scene.remove(effect.mesh);
          effect.mesh.geometry.dispose();
          effect.mesh.material.dispose();
          abilityEffects.splice(i, 1);
        }
      }

      sampleClock += dt;
      if (sampleClock > 0.3) {
        sampleClock = 0;
        const sideVelocity =
          player.vel.x * Math.cos(yaw) - player.vel.z * Math.sin(yaw);
        playerMotionSamples.push(Math.sign(sideVelocity));
        if (playerMotionSamples.length > 18) playerMotionSamples.shift();
        playerAttackSamples = Math.max(0, playerAttackSamples - 1);
      }

      if (noticeTimer > 0) {
        noticeTimer -= dt;
        if (noticeTimer <= 0) {
          document.getElementById('notice').textContent = '';
        }
      }

      updateHUD();
      renderer.render(scene, camera);
    }

    updateSlapCounter();
    updateTotalKills();
    const startupUnlocks = unlockAffordableGloves();
    if (startupUnlocks.length > 0) {
      showNotice(
        `Glove${startupUnlocks.length > 1 ? 's' : ''} unlocked: ${startupUnlocks.join(', ')}!`
      );
    }
    requestAnimationFrame(animate);

    addEventListener('resize', () => {
      camera.aspect = innerWidth / innerHeight;
      camera.updateProjectionMatrix();
      renderer.setSize(innerWidth, innerHeight);
    });
  </script>
</body>
</html>

