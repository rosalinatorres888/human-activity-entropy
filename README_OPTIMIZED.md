import React, { useState, useEffect } from 'react';
import { LineChart, Line, XAxis, YAxis, CartesianGrid, Tooltip, Legend, ResponsiveContainer, ScatterChart, Scatter, ReferenceLine } from 'recharts';

const JensenShannonComplexity = () => {
  const [selectedBehavior, setSelectedBehavior] = useState('all');
  const [showTrajectory, setShowTrajectory] = useState(false);

  // Generate the theoretical Jensen-Shannon complexity curve
  const generateComplexityCurve = () => {
    const points = [];
    for (let h = 0; h <= 1; h += 0.01) {
      // Theoretical JS complexity curve (approximation)
      const complexity = h <= 0.5 ? 
        2 * h * (1 - h) * Math.log(2) : 
        2 * (1 - h) * h * Math.log(2);
      points.push({ 
        entropy: h, 
        complexity: Math.max(0, complexity),
        type: 'theoretical'
      });
    }
    return points;
  };

  // Human behavior patterns on the complexity-entropy plane
  const behaviorPatterns = {
    healthy: {
      name: 'Healthy Lifestyle',
      color: '#22c55e',
      points: [
        { entropy: 0.65, complexity: 0.45, description: 'Structured but flexible routine' },
        { entropy: 0.62, complexity: 0.48, description: 'Varied activities with purpose' },
        { entropy: 0.68, complexity: 0.42, description: 'Adaptive daily patterns' }
      ]
    },
    depressed: {
      name: 'Depression',
      color: '#3b82f6',
      points: [
        { entropy: 0.25, complexity: 0.15, description: 'Highly predictable, low activity' },
        { entropy: 0.28, complexity: 0.12, description: 'Rigid, minimal variation' },
        { entropy: 0.22, complexity: 0.18, description: 'Repetitive patterns' }
      ]
    },
    manic: {
      name: 'Manic Episode',
      color: '#ef4444',
      points: [
        { entropy: 0.85, complexity: 0.25, description: 'Highly chaotic, impulsive' },
        { entropy: 0.88, complexity: 0.22, description: 'Random activity bursts' },
        { entropy: 0.82, complexity: 0.28, description: 'Erratic behavior patterns' }
      ]
    },
    elderly: {
      name: 'Healthy Aging',
      color: '#f59e0b',
      points: [
        { entropy: 0.45, complexity: 0.35, description: 'Consistent but structured' },
        { entropy: 0.48, complexity: 0.32, description: 'Regular routine with variation' },
        { entropy: 0.42, complexity: 0.38, description: 'Predictable but complex' }
      ]
    },
    cognitive_decline: {
      name: 'Cognitive Decline',
      color: '#8b5cf6',
      points: [
        { entropy: 0.35, complexity: 0.08, description: 'Simplified patterns' },
        { entropy: 0.32, complexity: 0.05, description: 'Reduced complexity' },
        { entropy: 0.38, complexity: 0.12, description: 'Loss of behavioral richness' }
      ]
    },
    athlete: {
      name: 'Elite Athlete',
      color: '#06b6d4',
      points: [
        { entropy: 0.55, complexity: 0.52, description: 'Complex training patterns' },
        { entropy: 0.58, complexity: 0.48, description: 'Structured high-intensity' },
        { entropy: 0.52, complexity: 0.55, description: 'Optimized complexity' }
      ]
    }
  };

  // Generate trajectory data showing how behavior changes over time
  const generateTrajectory = () => {
    const trajectory = [];
    // Simulate someone going from healthy to depressed to recovery
    const phases = [
      { start: { entropy: 0.65, complexity: 0.45 }, end: { entropy: 0.25, complexity: 0.15 }, phase: 'decline' },
      { start: { entropy: 0.25, complexity: 0.15 }, end: { entropy: 0.35, complexity: 0.25 }, phase: 'intervention' },
      { start: { entropy: 0.35, complexity: 0.25 }, end: { entropy: 0.62, complexity: 0.42 }, phase: 'recovery' }
    ];
    
    phases.forEach((phase, phaseIndex) => {
      for (let i = 0; i <= 20; i++) {
        const t = i / 20;
        const entropy = phase.start.entropy + t * (phase.end.entropy - phase.start.entropy);
        const complexity = phase.start.complexity + t * (phase.end.complexity - phase.start.complexity);
        trajectory.push({
          entropy,
          complexity,
          phase: phase.phase,
          time: phaseIndex * 21 + i,
          type: 'trajectory'
        });
      }
    });
    return trajectory;
  };

  const complexityCurve = generateComplexityCurve();
  const trajectory = generateTrajectory();

  const getVisiblePoints = () => {
    let points = [];
    
    if (selectedBehavior === 'all') {
      Object.values(behaviorPatterns).forEach(pattern => {
        points = points.concat(pattern.points.map(p => ({
          ...p,
          name: pattern.name,
          color: pattern.color
        })));
      });
    } else {
      points = behaviorPatterns[selectedBehavior].points.map(p => ({
        ...p,
        name: behaviorPatterns[selectedBehavior].name,
        color: behaviorPatterns[selectedBehavior].color
      }));
    }
    
    return points;
  };

  const CustomTooltip = ({ active, payload, label }) => {
    if (active && payload && payload.length) {
      const data = payload[0].payload;
      return (
        <div className="bg-white p-3 border border-gray-300 rounded shadow-lg">
          <p className="font-semibold">{data.name}</p>
          <p className="text-sm">Entropy: {data.entropy?.toFixed(3)}</p>
          <p className="text-sm">Complexity: {data.complexity?.toFixed(3)}</p>
          {data.description && <p className="text-xs text-gray-600 mt-1">{data.description}</p>}
        </div>
      );
    }
    return null;
  };

  return (
    <div className="w-full h-screen bg-gray-100 p-6">
      <div className="max-w-7xl mx-auto">
        <div className="bg-white rounded-lg shadow-lg p-6 mb-6">
          <h1 className="text-2xl font-bold text-gray-800 mb-2">
            Jensen-Shannon Complexity Plane
          </h1>
          <p className="text-gray-600 mb-4">
            Interactive visualization of human activity entropy vs. statistical complexity
          </p>
          
          <div className="flex flex-wrap gap-4 mb-6">
            <div className="space-y-2">
              <label className="block text-sm font-medium text-gray-700">
                Behavioral Pattern
              </label>
              <select
                value={selectedBehavior}
                onChange={(e) => setSelectedBehavior(e.target.value)}
                className="px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500"
              >
                <option value="all">All Patterns</option>
                {Object.entries(behaviorPatterns).map(([key, pattern]) => (
                  <option key={key} value={key}>{pattern.name}</option>
                ))}
              </select>
            </div>
            
            <div className="flex items-end">
              <button
                onClick={() => setShowTrajectory(!showTrajectory)}
                className={`px-4 py-2 rounded-md font-medium transition-colors ${
                  showTrajectory 
                    ? 'bg-blue-600 text-white' 
                    : 'bg-gray-200 text-gray-700 hover:bg-gray-300'
                }`}
              >
                {showTrajectory ? 'Hide' : 'Show'} Trajectory
              </button>
            </div>
          </div>
        </div>

        <div className="bg-white rounded-lg shadow-lg p-6">
          <div className="h-96">
            <ResponsiveContainer width="100%" height="100%">
              <ScatterChart margin={{ top: 20, right: 30, bottom: 40, left: 40 }}>
                <CartesianGrid strokeDasharray="3 3" />
                <XAxis 
                  type="number" 
                  dataKey="entropy" 
                  domain={[0, 1]}
                  label={{ value: 'Normalized Entropy', position: 'insideBottom', offset: -20 }}
                />
                <YAxis 
                  type="number" 
                  dataKey="complexity" 
                  domain={[0, 0.6]}
                  label={{ value: 'Statistical Complexity', angle: -90, position: 'insideLeft' }}
                />
                <Tooltip content={<CustomTooltip />} />
                
                {/* Theoretical complexity curve */}
                <Line 
                  type="monotone" 
                  dataKey="complexity" 
                  stroke="#6b7280" 
                  strokeWidth={2}
                  strokeDasharray="5 5"
                  dot={false}
                  data={complexityCurve}
                />
                
                {/* Behavior patterns */}
                {selectedBehavior === 'all' ? (
                  Object.entries(behaviorPatterns).map(([key, pattern]) => (
                    <Scatter
                      key={key}
                      name={pattern.name}
                      data={pattern.points}
                      fill={pattern.color}
                      stroke={pattern.color}
                      strokeWidth={2}
                    />
                  ))
                ) : (
                  <Scatter
                    name={behaviorPatterns[selectedBehavior].name}
                    data={getVisiblePoints()}
                    fill={behaviorPatterns[selectedBehavior].color}
                    stroke={behaviorPatterns[selectedBehavior].color}
                    strokeWidth={2}
                  />
                )}
                
                {/* Trajectory */}
                {showTrajectory && (
                  <Line
                    type="monotone"
                    dataKey="complexity"
                    stroke="#dc2626"
                    strokeWidth={3}
                    dot={{ fill: '#dc2626', r: 2 }}
                    data={trajectory}
                  />
                )}
              </ScatterChart>
            </ResponsiveContainer>
          </div>
          
          <div className="mt-6 grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
            <div className="bg-blue-50 p-4 rounded-lg">
              <h3 className="font-semibold text-blue-800 mb-2">Low Entropy, Low Complexity</h3>
              <p className="text-sm text-blue-700">
                Rigid routines, predictable patterns (Depression, Cognitive Decline)
              </p>
            </div>
            
            <div className="bg-green-50 p-4 rounded-lg">
              <h3 className="font-semibold text-green-800 mb-2">Moderate Entropy, High Complexity</h3>
              <p className="text-sm text-green-700">
                Optimal zone: Structured but flexible (Healthy Lifestyle, Athletes)
              </p>
            </div>
            
            <div className="bg-red-50 p-4 rounded-lg">
              <h3 className="font-semibold text-red-800 mb-2">High Entropy, Low Complexity</h3>
              <p className="text-sm text-red-700">
                Chaotic behavior, random patterns (Manic Episodes, Substance Abuse)
              </p>
            </div>
          </div>
          
          <div className="mt-6 p-4 bg-gray-50 rounded-lg">
            <h3 className="font-semibold text-gray-800 mb-2">Mathematical Interpretation</h3>
            <div className="grid grid-cols-1 md:grid-cols-2 gap-4 text-sm text-gray-700">
              <div>
                <strong>Entropy (H):</strong> Measures randomness/unpredictability<br/>
                <strong>Complexity (C):</strong> Measures structured information content
              </div>
              <div>
                <strong>Optimal Health:</strong> Balanced entropy with high complexity<br/>
                <strong>Pathological States:</strong> Extreme entropy with low complexity
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  );
};

export default JensenShannonComplexity;