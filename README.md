disp('SCARA_V3')

syms a1 a2 a3 a4

%% Link lengths

a1 = 5;

a2 = 10;

a3 = 5;

a4 = 10;

%% D-H Parameters [theta, d, r, alpha, offset]

% if prismatic joint: theta = theta, d = 0, offset = 1, after offset put the value if d

% if revolute joint: theta = 0, offset = 0, after offset put the value of theta

H0_1 = Link([0,0,0,0,1,a1]);

H0_1.qlim = [0 30];

H0_2 = Link([0,0,a2,0,0]);

H0_2.qlim = pi/180*[-90 90];

H0_3 = Link([0,a3,a4,0,0]);

H0_3.qlim = pi/180*[-90 90];

Scara_V3 = SerialLink([H0_1 H1_2 H2_3], 'name', 'SCARA_V3')

Scara_V3.plot([0 0 0], 'workspace', [-5 30 -30 30 0 30])

Scara_V3.teach

%% Forward Kinematics 

%syntax: FK = robot_variable.fkine(joint_variables)

Af = ([5,pi/2,pi/2]); %joint_variables FK = Scara_V3.fkine(AF)
