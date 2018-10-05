model Hydraulics
  package Medium = Modelica.Media.Water.ConstantPropertyLiquidWater;
  
  inner Modelica.Fluid.System system annotation(
    Placement(visible = true, transformation(origin = {-50, 86}, extent = {{-10, -10}, {10, 10}}, rotation = 0)));
  Modelica.Fluid.Sources.Boundary_pT source(redeclare package Medium= Medium,T = system.T_ambiente, p = 2.5e5)  annotation(
    Placement(visible = true, transformation(origin = {-12, 78}, extent = {{-10, -10}, {10, 10}}, rotation = 0)));
  Modelica.Fluid.Sources.Boundary_pT ambiente annotation(
    Placement(visible = true, transformation(origin = {-68, -32}, extent = {{-10, -10}, {10, 10}}, rotation = 0)));
  Modelica.Fluid.Valves.ValveDiscrete valveDiscrete1(redeclare package Medium= Medium,dp_nominal = 100000, m_flow_nominal = 40)  annotation(
    Placement(visible = true, transformation(origin = {30, 82}, extent = {{-10, -10}, {10, 10}}, rotation = 0)));
  Modelica.Fluid.Valves.ValveDiscrete valveDiscrete2(redeclare package Medium= Medium,dp_nominal = 100000, m_flow_nominal = 100)  annotation(
    Placement(visible = true, transformation(origin = {74, -12}, extent = {{10, -10}, {-10, 10}}, rotation = 90)));
  Modelica.Fluid.Valves.ValveDiscrete valveDiscrete3(m_flow_nominal = 10)  annotation(
    Placement(visible = true, transformation(origin = {38, -68}, extent = {{10, -10}, {-10, 10}}, rotation = 0)));
  Modelica.Fluid.Vessels.OpenTank tank(crossArea = 5, height = 6, level_start = 0.05, nPorts = 2, use_portsData = false)  annotation(
    Placement(visible = true, transformation(origin = {92, 58}, extent = {{-20, -20}, {20, 20}}, rotation = 0)));
  Modelica.Fluid.Vessels.OpenTank tank1(crossArea = 6, height = 8, level_start = 0.05, nPorts = 2)  annotation(
    Placement(visible = true, transformation(origin = {122, -66}, extent = {{-20, -20}, {20, 20}}, rotation = 0)));
equation
  connect(valveDiscrete3.port_b, ambiente.ports[1]) annotation(
    Line(points = {{28, -68}, {-58, -68}, {-58, -32}, {-58, -32}}, color = {0, 127, 255}));
  connect(valveDiscrete3.port_a, tank1.ports[2]) annotation(
    Line(points = {{48, -68}, {124, -68}, {124, -86}, {122, -86}}, color = {0, 127, 255}));
  connect(valveDiscrete2.port_b, tank1.ports[1]) annotation(
    Line(points = {{74, -22}, {120, -22}, {120, -86}, {122, -86}}, color = {0, 127, 255}));
  connect(valveDiscrete2.port_a, tank.ports[2]) annotation(
    Line(points = {{74, -2}, {92, -2}, {92, 38}, {92, 38}}, color = {0, 127, 255}));
  connect(valveDiscrete1.port_b, tank.ports[1]) annotation(
    Line(points = {{40, 82}, {54, 82}, {54, 38}, {92, 38}}, color = {0, 127, 255}));
  connect(valveDiscrete1.port_a, source.ports[1]) annotation(
    Line(points = {{20, 82}, {-2, 82}, {-2, 78}, {-2, 78}}, color = {0, 127, 255}));
  annotation(
    uses(Modelica(version = "3.2.2")));
end Hydraulics;
