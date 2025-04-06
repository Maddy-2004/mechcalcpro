<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>MechCalc Pro</title>
  <style>
    /* Ensure html and body take up full height */
    html, body {
      margin: 0;
      padding: 0;
      height: 100%;
      font-family: Arial, sans-serif;
    }

    /* Overall body background (used for the intro screen) */
    body {
      background: #f4f4f4;
      color: #333;
    }

    /* Container style shared by the intro screen */
    .container {
      width: 90%;
      max-width: 1200px;
      background: #fff;
      padding: 20px;
      margin: 20px auto;
      border-radius: 8px;
      box-shadow: 0 4px 8px rgba(0,0,0,0.1);
    }

    h1, h2, h3 {
      text-align: center;
      margin-top: 0;
    }

    p {
      line-height: 1.6;
    }

    /* Intro Screen Button */
    .btn {
      background-color: #007BFF;
      color: #fff;
      border: none;
      padding: 12px 24px;
      margin: 20px auto; /* Center the button */
      border-radius: 4px;
      font-size: 16px;
      cursor: pointer;
      transition: background 0.3s ease;
      display: block;
      width: fit-content;
    }
    .btn:hover {
      background-color: #0056b3;
    }

    /* ------------------------------
       SECOND SCREEN: Full Screen
       ------------------------------ */
    #calcPage {
      /* Make the second screen fill the entire browser window */
      position: fixed; /* or absolute, but fixed ensures it stays full screen */
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: #fff;
      /* Hide it by default, then reveal when needed */
      display: none;
      overflow-y: auto; /* in case the content grows taller than the screen */
    }

    /* We can keep a container look inside the second screen
       if you want some padding or structure, but remove
       margin/box-shadow so it’s flush to the edges. */
    #calcPage .container {
      margin: 0;
      max-width: 100%;
      height: auto;
      border-radius: 0;
      box-shadow: none;
      padding: 20px; /* optional: keep some padding for content spacing */
    }

    .second-page-content {
      display: flex;
      flex-direction: row;
      gap: 20px;
      margin-top: 20px;
    }

    /* Sidebar styles */
    .sidebar {
      flex: 0 0 250px;
      background-color: #f8f9fa;
      border-right: 1px solid #ddd;
      padding: 10px;
      height: calc(100vh - 180px); /* adjust if needed for header/footer */
      overflow-y: auto;
    }

    .sidebar ul {
      list-style: none;
      padding: 0;
      margin: 0;
    }

    .sidebar li {
      padding: 10px;
      margin-bottom: 5px;
      cursor: pointer;
      border-radius: 4px;
      transition: background 0.3s ease;
    }
    .sidebar li:hover {
      background-color: #e2e6ea;
    }
    .sidebar li.active {
      background-color: #007BFF;
      color: #fff;
    }

    /* Main Content styles */
    .main-content {
      flex: 1;
      padding: 10px;
    }
    .main-content h2 {
      text-align: center;
      margin-top: 0;
    }

    /* Download buttons container */
    .download-buttons {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      margin-top: 20px;
      justify-content: center;
    }
    .download-btn {
      background-color: #17a2b8;
      color: #fff;
      text-decoration: none;
      padding: 10px 15px;
      border-radius: 4px;
      transition: background 0.3s ease;
    }
    .download-btn:hover {
      background-color: #138496;
    }

    /* Return to Home button styles */
    .return-home {
      background-color: #dc3545;
      color: #fff;
      border: none;
      padding: 10px 20px;
      border-radius: 4px;
      font-size: 14px;
      cursor: pointer;
      transition: background 0.3s ease;
      margin: 20px auto 0 auto;
      display: block;
    }
    .return-home:hover {
      background-color: #c82333;
    }

    /* Hide container */
    .hidden {
      display: none;
    }
  </style>
</head>
<body>
  <!-- Intro Screen -->
  <div id="introScreen" class="container">
    <h1><strong>Introducing MechCalc Pro</strong></h1>
    <p>
      MechCalc Pro is an all-in-one suite designed for mechanical engineering professionals who demand precision and efficiency in every calculation. This comprehensive application brings together 11 specialized tools to perform 14 critical engineering calculations, ensuring you have everything you need to tackle even the most complex design challenges.
    </p>
    <h3><strong>Key Features</strong></h3>
    <p>
      <strong>Broad Calculation Capabilities:</strong><br>
      - <strong>Degree Of Freedom (DOF) Calculations:</strong> Determine the movement possibilities of your system with ease.<br>
      - <strong>DH Parameters:</strong> Compute Denavit-Hartenberg parameters for precise robotic arm modeling.<br>
      - <strong>Forward and Inverse Kinematics:</strong><br>
      &nbsp;&nbsp;&nbsp;&nbsp;• <strong>Forward Kinematics:</strong> Calculate the end-effector positions and verify them using inverse kinematics to ensure robust accuracy.<br>
      &nbsp;&nbsp;&nbsp;&nbsp;• <strong>Inverse Kinematics:</strong> Determine joint parameters for a desired end-effector position, with verification via forward kinematics.<br>
      - <strong>Homogeneous Transformations:</strong><br>
      &nbsp;&nbsp;&nbsp;&nbsp;• <strong>2D and 3D Transformations:</strong> Seamlessly convert between coordinate frames in both two and three dimensions.<br>
      - <strong>Dynamics and Jacobian Analysis:</strong><br>
      &nbsp;&nbsp;&nbsp;&nbsp;• Dive into dynamic system analysis and compute the Jacobian matrix for advanced robotics and mechanism evaluations.<br>
      - <strong>Rotation Matrices:</strong><br>
      &nbsp;&nbsp;&nbsp;&nbsp;• Analyze rotations with dedicated tools for both 2D and 3D scenarios.
    </p>
    <p>
      <strong>Integrated Mechanical Calculations Module:</strong><br>
      A single, powerful module within MechCalc Pro unifies calculations for mechanical part analysis, including:<br>
      - <strong>Shear:</strong> Assess the shear forces within materials and structures.<br>
      - <strong>Stress:</strong> Evaluate stress distributions to ensure structural integrity.<br>
      - <strong>Heat Applications:</strong> Analyze thermal effects on materials and mechanical systems.<br>
      - <strong>Tensile:</strong> Perform tensile analysis to determine material strength and durability.<br>
      This integration ensures that all related computations are consistent and interlinked, providing a holistic view of your engineering problem.
    </p>
    <p>
      <strong>Why Choose MechCalc Pro?</strong><br>
      - <strong>Validated Results:</strong> Every calculation, especially in kinematics, is cross-verified to eliminate errors and instill confidence in your design decisions.<br>
      - <strong>User-Friendly Interface:</strong> Despite its robust features, MechCalc Pro is engineered with simplicity in mind, allowing both seasoned professionals and newcomers to perform sophisticated calculations effortlessly.<br>
      - <strong>Streamlined Workflow:</strong> Reduce the time spent on complex computations and focus more on design innovation and problem-solving.
    </p>
    <p>
      MechCalc Pro is not just a tool—it's a trusted partner in your engineering projects, designed to elevate the quality and efficiency of your work. Whether you're optimizing a robotic system, evaluating structural integrity, or conducting detailed mechanical part analysis, MechCalc Pro delivers the precise data you need to succeed.
    </p>
    <p>
      Feel free to explore the full suite and experience the power of integrated mechanical calculations at your fingertips.
    </p>
    <button class="btn" onclick="startCalculating()">Start Calculating</button>
  </div>

  <!-- Second Screen: List of the calculations -->
  <div id="calcPage">
    <div class="container">
      <h1>List of the calculations</h1>
      <div class="second-page-content">
        <!-- Sidebar -->
        <div class="sidebar">
          <ul>
            <li onclick="selectCalculation(this, 'DH Parameters')">DH Parameters</li>
            <li onclick="selectCalculation(this, 'DOF - Degree Of Freedom')">DOF - Degree Of Freedom</li>
            <li onclick="selectCalculation(this, 'Dynamics')">Dynamics</li>
            <li onclick="selectCalculation(this, 'Forward Kinematics')">Forward Kinematics</li>
            <li onclick="selectCalculation(this, 'General Mechanical Calculations')">General Mechanical Calculations</li>
            <li onclick="selectCalculation(this, 'Homogenous transformation in 2d')">Homogenous transformation in 2d</li>
            <li onclick="selectCalculation(this, 'Homogenous transformation in 3d')">Homogenous transformation in 3d</li>
            <li onclick="selectCalculation(this, 'Inverse Kinematics')">Inverse Kinematics</li>
            <li onclick="selectCalculation(this, 'Jacobian')">Jacobian</li>
            <li onclick="selectCalculation(this, 'Rotation matrix in 2d')">Rotation matrix in 2d</li>
            <li onclick="selectCalculation(this, 'Rotation matrix in 3d')">Rotation matrix in 3d</li>
          </ul>
        </div>
        <!-- Main Content -->
        <div class="main-content">
          <h2 id="calcTitle">Select a Calculation</h2>
          <div id="calcInputs">
            <p>Please select a calculation from the sidebar.</p>
          </div>
        </div>
      </div>
      <button class="return-home" onclick="returnHome()">Return to Home</button>
    </div>
  </div>

  <script>
    // Mapping each calculation to its specific download links.
    const downloadLinks = {
      "DH Parameters": {
        windows: "https://github.com/Maddy-2004/mechcalcpro/releases/download/V1.0/DH.Para.exe",
        android: "https://github.com/Maddy-2004/mechcalcpro/releases/download/V1.0/DH.Para.apk"
      },
      "DOF - Degree Of Freedom": {
        windows: "https://github.com/Maddy-2004/mechcalcpro/releases/download/V1.0/DOF.exe",
        android: "https://github.com/Maddy-2004/mechcalcpro/releases/download/V1.0/DOF.apk"
      },
      "Dynamics": {
        windows: "https://github.com/Maddy-2004/Mech-App/releases/download/v1.0/Dynamics.exe",
        android: "https://github.com/Maddy-2004/Mech-App/releases/download/v1.0/Dynamics.apk"
      },
      "Forward Kinematics": {
        windows: "https://github.com/Maddy-2004/Mech-App/releases/download/v1.0/Forward.Kinematics.exe",
        android: "https://github.com/Maddy-2004/Mech-App/releases/download/v1.0/Forward.Kinematics.apk"
      },
      "General Mechanical Calculations": {
        windows: "https://github.com/Maddy-2004/Mech-App/releases/download/v1.0/General.Mech.Calculations.exe",
        android: "https://github.com/Maddy-2004/Mech-App/releases/download/v1.0/General.Mech.Calculations.apk"
      },
      "Homogenous transformation in 2d": {
        windows: "https://github.com/Maddy-2004/Mech-App/releases/download/v1.0/Homo_2d.exe",
        android: "https://github.com/Maddy-2004/Mech-App/releases/download/v1.0/Homo_2d.apk"
      },
      "Homogenous transformation in 3d": {
        windows: "https://github.com/Maddy-2004/Mech-App/releases/download/v1.0/Homo_3d.exe",
        android: "https://github.com/Maddy-2004/Mech-App/releases/download/v1.0/Homo_3d.apk"
      },
      "Inverse Kinematics": {
        windows: "https://github.com/Maddy-2004/Mech-App/releases/download/v1.0/Inverse.Kinematics.exe",
        android: "https://github.com/Maddy-2004/Mech-App/releases/download/v1.0/Inverse.Kinematics.apk"
      },
      "Jacobian": {
        windows: "https://github.com/Maddy-2004/Mech-App/releases/download/v1.0/Jacobian.exe",
        android: "https://github.com/Maddy-2004/Mech-App/releases/download/v1.0/Jacobian.apk"
      },
      "Rotation matrix in 2d": {
        windows: "https://github.com/Maddy-2004/Mech-App/releases/download/v1.0/Rotation.matrix.in.2d.exe",
        android: "https://github.com/Maddy-2004/Mech-App/releases/download/v1.0/Rotation.matrix.in.2d.apk"
      },
      "Rotation matrix in 3d": {
        windows: "https://github.com/Maddy-2004/Mech-App/releases/download/v1.0/Rotation.matrix.in.3d.exe",
        android: "https://github.com/Maddy-2004/Mech-App/releases/download/v1.0/Rotation.matrix.in.3d.apk"
      }
    };

    function startCalculating() {
      // Hide the intro screen container
      document.getElementById('introScreen').style.display = 'none';
      // Show the calcPage (full screen)
      document.getElementById('calcPage').style.display = 'block';
    }
    
    // Function to handle selection of a calculation from the sidebar
    function selectCalculation(element, title) {
      // Remove active class from all sidebar items
      var items = document.querySelectorAll('.sidebar li');
      items.forEach(function(item) {
        item.classList.remove('active');
      });
      // Add active class to the clicked item
      element.classList.add('active');
      // Update the heading in the main content
      document.getElementById('calcTitle').innerText = title;
      
      // Retrieve the download links for the selected calculation
      const links = downloadLinks[title];
      let downloadHTML = '';
      if (links) {
        downloadHTML = '<div class="download-buttons">' +
                         '<a href="' + links.windows + '" target="_blank" class="download-btn">Download for Windows</a>' +
                         '<a href="' + links.android + '" target="_blank" class="download-btn">Download for Android</a>' +
                       '</div>';
      } else {
        downloadHTML = '<p>No downloads available for this calculation.</p>';
      }
      
      // Update the input fields placeholder and add download buttons
      document.getElementById('calcInputs').innerHTML = 
        '<p>Input fields for ' + title + ' go here.</p>' + downloadHTML;
    }
    
    // Function to return to the intro (home) page
    function returnHome() {
      location.reload();
    }
  </script>
</body>
</html>
