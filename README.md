
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=1280, initial-scale=1.0">
  <title>Razorpay AI Bootcamp 2026</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&family=JetBrains+Mono:wght@400;500;600&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <style>
    :root {
      --bg-primary: #040814;
      --bg-secondary: #0D1527;
      --border-slate: #1E293B;
      --brand-blue: #0052FF;
      --tech-teal: #0D94FB;
      --success: #10B981;
      --alert: #F59E0B;
      --text-primary: #F1F5F9;
      --text-secondary: #94A3B8;
      --text-muted: #64748B;
      --gradient-accent: linear-gradient(135deg, #0052FF 0%, #0D94FB 100%);
      --gradient-text: linear-gradient(135deg, #0052FF 0%, #0D94FB 50%, #10B981 100%);
    }
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    html, body {
      width: 100vw;
      height: 100vh;
      overflow: hidden;
      background: var(--bg-primary);
      font-family: 'Plus Jakarta Sans', sans-serif;
      color: var(--text-primary);
    }
    .deck-container {
      width: 100vw;
      height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      background: var(--bg-primary);
    }
    .slide-wrapper {
      width: 1280px;
      height: 720px;
      position: relative;
      overflow: hidden;
      background: var(--bg-primary);
    }
    .slide-container {
      width: 1280px;
      height: 720px;
      position: absolute;
      top: 0;
      left: 0;
      padding: 20px 32px;
      display: none;
      opacity: 0;
      transition: opacity 0.4s ease;
      background: radial-gradient(circle at 100% 0%, rgba(13, 148, 251, 0.08) 0%, transparent 40%),
                  radial-gradient(circle at 0% 100%, rgba(0, 82, 255, 0.05) 0%, transparent 40%);
    }
    .slide-container.active {
      display: block;
      opacity: 1;
    }
    /* Navigation */
    .nav-controls {
      position: fixed;
      bottom: 24px;
      right: 32px;
      display: flex;
      gap: 8px;
      z-index: 1000;
    }
    .nav-btn {
      width: 40px;
      height: 40px;
      border-radius: 10px;
      border: 1px solid var(--border-slate);
      background: var(--bg-secondary);
      color: var(--text-secondary);
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
      transition: all 0.2s ease;
      font-size: 14px;
    }
    .nav-btn:hover {
      border-color: var(--tech-teal);
      color: var(--text-primary);
      transform: translateY(-2px);
    }
    .slide-counter {
      position: fixed;
      bottom: 24px;
      left: 32px;
      font-family: 'JetBrains Mono', monospace;
      font-size: 12px;
      color: var(--text-muted);
      z-index: 1000;
      letter-spacing: 1px;
    }
    /* Utilities */
    .gradient-text {
      background: var(--gradient-text);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }
    .badge {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      padding: 4px 10px;
      border-radius: 6px;
      font-size: 11px;
      font-weight: 600;
      letter-spacing: 0.5px;
      text-transform: uppercase;
    }
    .badge-brand {
      background: rgba(0, 82, 255, 0.15);
      color: var(--brand-blue);
      border: 1px solid rgba(0, 82, 255, 0.3);
    }
    .badge-success {
      background: rgba(16, 185, 129, 0.15);
      color: var(--success);
      border: 1px solid rgba(16, 185, 129, 0.3);
    }
    .badge-alert {
      background: rgba(245, 158, 11, 0.15);
      color: var(--alert);
      border: 1px solid rgba(245, 158, 11, 0.3);
    }
    .card {
      background: var(--bg-secondary);
      border: 1px solid var(--border-slate);
      border-radius: 12px;
      padding: 16px;
      transition: all 0.2s ease;
    }
    .card:hover {
      border-color: rgba(13, 148, 251, 0.4);
      transform: translateY(-2px);
      box-shadow: 0 8px 32px rgba(0, 82, 255, 0.1);
    }
    .terminal {
      background: #0a0f1e;
      border: 1px solid var(--border-slate);
      border-radius: 10px;
      overflow: hidden;
    }
    .terminal-header {
      display: flex;
      align-items: center;
      gap: 8px;
      padding: 10px 14px;
      background: rgba(30, 41, 59, 0.5);
      border-bottom: 1px solid var(--border-slate);
    }
    .terminal-dot {
      width: 10px;
      height: 10px;
      border-radius: 50%;
    }
    .terminal-dot.red { background: #EF4444; }
    .terminal-dot.yellow { background: #F59E0B; }
    .terminal-dot.green { background: #10B981; }
    .terminal-body {
      padding: 10px 12px;
      font-family: 'JetBrains Mono', monospace;
      font-size: 11px;
      line-height: 1.6;
      color: var(--text-secondary);
    }
    .terminal-body .cmd { color: var(--tech-teal); }
    .terminal-body .output { color: var(--text-secondary); }
    .terminal-body .success { color: var(--success); }
    .terminal-body .highlight { color: var(--alert); }
    .section-title {
      font-size: 13px;
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: 1.5px;
      color: var(--text-muted);
      margin-bottom: 12px;
    }
    .section-title span {
      color: var(--tech-teal);
    }
    /* Slide 1: Welcome */
    .slide-1 {
      display: flex;
      gap: 20px;
    }
    .slide-1-left {
      flex: 1;
      display: flex;
      flex-direction: column;
      justify-content: center;
      gap: 14px;
    }
    .brand-label {
      display: flex;
      align-items: center;
      gap: 10px;
      font-size: 12px;
      font-weight: 700;
      letter-spacing: 2px;
      color: var(--tech-teal);
      text-transform: uppercase;
    }
    .brand-label i {
      font-size: 16px;
      color: var(--brand-blue);
    }
    .main-title {
      font-size: 52px;
      font-weight: 800;
      line-height: 1.1;
      letter-spacing: -1px;
    }
    .meta-line {
      font-family: 'JetBrains Mono', monospace;
      font-size: 13px;
      color: var(--text-secondary);
      display: flex;
      align-items: center;
      gap: 8px;
    }
    .slide-1-right {
      width: 420px;
      display: flex;
      flex-direction: column;
      gap: 10px;
    }
    .profile-widget {
      background: var(--bg-secondary);
      border: 1px solid var(--border-slate);
      border-radius: 10px;
      padding: 10px 14px;
    }
    .profile-widget h3 {
      font-size: 12px;
      font-weight: 700;
      margin-bottom: 4px;
      color: var(--text-primary);
    }
    .stat-row {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 4px 0;
      border-bottom: 1px solid var(--border-slate);
    }
    .stat-row:last-child { border-bottom: none; }
    .stat-label {
      font-size: 11px;
      color: var(--text-secondary);
    }
    .stat-value {
      font-family: 'JetBrains Mono', monospace;
      font-size: 11px;
      font-weight: 600;
      color: var(--tech-teal);
    }
    .outcomes-list {
      display: flex;
      flex-direction: column;
      gap: 5px;
    }
    .outcome-item {
      display: flex;
      align-items: center;
      gap: 8px;
      padding: 6px 10px;
      background: rgba(0, 82, 255, 0.08);
      border: 1px solid rgba(0, 82, 255, 0.2);
      border-radius: 6px;
      font-size: 12px;
      font-weight: 600;
    }
    .outcome-item i {
      color: var(--success);
      font-size: 11px;
    }
    .section-title {
      font-size: 11px;
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: 1.5px;
      color: var(--text-muted);
      margin-bottom: 6px;
    }
    .section-title span {
      color: var(--tech-teal);
    }
    /* Slide 2: What Is AI */
    .slide-2 {
      display: flex;
      flex-direction: column;
      gap: 16px;
    }
    .slide-2-header {
      text-align: center;
    }
    .slide-2-header h2 {
      font-size: 28px;
      font-weight: 800;
      margin-bottom: 4px;
    }
    .slide-2-header p {
      font-size: 14px;
      color: var(--text-secondary);
    }
    .values-bar {
      display: flex;
      justify-content: center;
      gap: 10px;
      flex-wrap: wrap;
      margin-top: 8px;
    }
    .value-chip {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      padding: 5px 12px;
      border-radius: 8px;
      font-size: 12px;
      font-weight: 600;
      background: rgba(0, 82, 255, 0.1);
      border: 1px solid rgba(0, 82, 255, 0.25);
      color: var(--text-primary);
      transition: all 0.2s ease;
    }
    .value-chip:hover {
      border-color: var(--tech-teal);
      transform: translateY(-2px);
    }
    .value-chip i {
      color: var(--tech-teal);
      font-size: 11px;
    }
    .card-grid {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 12px;
      flex: 1;
    }
    .feature-card {
      background: var(--bg-secondary);
      border: 1px solid var(--border-slate);
      border-radius: 12px;
      padding: 20px;
      display: flex;
      flex-direction: column;
      gap: 12px;
      transition: all 0.2s ease;
      cursor: pointer;
    }
    .feature-card:hover {
      border-color: var(--tech-teal);
      transform: translateY(-3px);
    }
    .feature-icon {
      width: 40px;
      height: 40px;
      border-radius: 10px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 18px;
      background: var(--gradient-accent);
      color: white;
    }
    .feature-card h3 {
      font-size: 16px;
      font-weight: 700;
    }
    .feature-card p {
      font-size: 13px;
      color: var(--text-secondary);
      line-height: 1.5;
    }
    .callout-panel {
      background: linear-gradient(135deg, rgba(0, 82, 255, 0.1) 0%, rgba(13, 148, 251, 0.1) 100%);
      border: 1px solid rgba(0, 82, 255, 0.3);
      border-radius: 12px;
      padding: 16px 24px;
      display: flex;
      align-items: center;
      gap: 12px;
      font-size: 14px;
      font-weight: 600;
    }
    .callout-panel i {
      color: var(--alert);
      font-size: 20px;
    }
    /* Slide 3: Why AI Matters */
    .slide-3 {
      display: flex;
      gap: 24px;
    }
    .slide-3-left {
      flex: 1;
      display: flex;
      flex-direction: column;
      gap: 10px;
    }
    .slide-3-left h2 {
      font-size: 24px;
      font-weight: 800;
      margin-bottom: 4px;
    }
    .benefit-tile {
      display: flex;
      gap: 14px;
      padding: 14px;
      background: var(--bg-secondary);
      border: 1px solid var(--border-slate);
      border-radius: 12px;
      transition: all 0.2s ease;
      cursor: pointer;
    }
    .benefit-tile:hover {
      border-color: var(--tech-teal);
    }
    .benefit-icon {
      width: 40px;
      height: 40px;
      min-width: 40px;
      border-radius: 10px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 18px;
      background: rgba(0, 82, 255, 0.15);
      color: var(--brand-blue);
    }
    .benefit-content h3 {
      font-size: 15px;
      font-weight: 700;
      margin-bottom: 3px;
    }
    .benefit-content p {
      font-size: 12px;
      color: var(--text-secondary);
      line-height: 1.4;
    }
    .slide-3-right {
      width: 420px;
      display: flex;
      flex-direction: column;
      gap: 10px;
    }
    .metrics-widget-horizontal {
      background: var(--bg-secondary);
      border: 1px solid var(--border-slate);
      border-radius: 12px;
      padding: 16px 20px;
      display: flex;
      flex-direction: row;
      align-items: center;
      justify-content: space-between;
      gap: 20px;
    }
    .metrics-h-left {
      display: flex;
      flex-direction: column;
      align-items: flex-start;
      gap: 6px;
      flex-shrink: 0;
    }
    .metrics-h-right {
      display: flex;
      flex-direction: column;
      align-items: flex-end;
      gap: 4px;
      flex: 1;
      text-align: right;
    }
    .big-counter {
      font-family: 'JetBrains Mono', monospace;
      font-size: 42px;
      font-weight: 700;
      background: var(--gradient-text);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      line-height: 1;
    }
    .metrics-context {
      font-size: 12px;
      color: var(--text-secondary);
      line-height: 1.5;
    }
    .ai-stack-panel {
      background: var(--bg-secondary);
      border: 1px solid var(--border-slate);
      border-radius: 12px;
      padding: 16px;
      display: flex;
      flex-direction: column;
      gap: 10px;
    }
    .stack-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 8px;
    }
    .stack-item {
      display: flex;
      align-items: center;
      gap: 8px;
      padding: 8px 10px;
      background: var(--bg-primary);
      border: 1px solid var(--border-slate);
      border-radius: 8px;
      font-size: 12px;
      font-weight: 600;
      color: var(--text-secondary);
      transition: all 0.2s ease;
    }
    .stack-item:hover {
      border-color: var(--tech-teal);
      color: var(--text-primary);
    }
    .stack-item i {
      color: var(--tech-teal);
      font-size: 13px;
    }
    /* Slide 4: Bootcamp Overview */
    .slide-4 {
      display: flex;
      flex-direction: column;
      gap: 16px;
    }
    .slide-4 h2 {
      font-size: 24px;
      font-weight: 800;
    }
    .timeline-container {
      display: flex;
      flex-direction: column;
      gap: 16px;
      flex: 1;
    }
    .timeline-progress {
      display: flex;
      align-items: center;
      gap: 8px;
      padding: 0 8px;
    }
    .progress-segment {
      height: 4px;
      flex: 1;
      border-radius: 2px;
      background: var(--border-slate);
    }
    .progress-segment.active {
      background: var(--gradient-accent);
    }
    .week-columns {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 14px;
      flex: 1;
    }
    .week-card {
      background: var(--bg-secondary);
      border: 1px solid var(--border-slate);
      border-radius: 12px;
      padding: 20px;
      display: flex;
      flex-direction: column;
      gap: 12px;
      transition: all 0.2s ease;
      cursor: pointer;
    }
    .week-card:hover {
      border-color: var(--tech-teal);
    }
    .week-header {
      display: flex;
      align-items: center;
      justify-content: space-between;
    }
    .week-number {
      font-family: 'JetBrains Mono', monospace;
      font-size: 11px;
      font-weight: 600;
      padding: 4px 10px;
      border-radius: 6px;
      background: rgba(0, 82, 255, 0.15);
      color: var(--brand-blue);
    }
    .week-dates {
      font-size: 11px;
      color: var(--text-muted);
      font-family: 'JetBrains Mono', monospace;
    }
    .week-card h3 {
      font-size: 18px;
      font-weight: 700;
    }
    .week-topics {
      display: flex;
      flex-direction: column;
      gap: 6px;
      flex: 1;
    }
    .week-topic {
      display: flex;
      align-items: center;
      gap: 8px;
      font-size: 13px;
      color: var(--text-secondary);
    }
    .week-topic i {
      font-size: 10px;
      color: var(--success);
    }
    .footer-alert {
      display: flex;
      align-items: center;
      gap: 10px;
      padding: 12px 16px;
      background: rgba(245, 158, 11, 0.1);
      border: 1px solid rgba(245, 158, 11, 0.25);
      border-radius: 10px;
      font-size: 13px;
      color: var(--alert);
    }
    /* Slide 5: How We Work */
    .slide-5 {
      display: flex;
      gap: 24px;
    }
    .slide-5-left {
      flex: 1;
      display: flex;
      flex-direction: column;
      gap: 12px;
    }
    .slide-5-left h2 {
      font-size: 24px;
      font-weight: 800;
    }
    .group-card {
      background: var(--bg-secondary);
      border: 1px solid var(--border-slate);
      border-radius: 12px;
      padding: 24px;
      display: flex;
      flex-direction: column;
      gap: 16px;
      flex: 1;
      justify-content: center;
    }
    .group-flow {
      display: flex;
      align-items: center;
      gap: 16px;
      justify-content: center;
    }
    .group-block {
      text-align: center;
      padding: 16px 20px;
      background: rgba(0, 82, 255, 0.1);
      border: 1px solid rgba(0, 82, 255, 0.3);
      border-radius: 10px;
    }
    .group-block .number {
      font-family: 'JetBrains Mono', monospace;
      font-size: 28px;
      font-weight: 700;
      color: var(--brand-blue);
    }
    .group-block .label {
      font-size: 12px;
      color: var(--text-secondary);
      margin-top: 4px;
    }
    .group-arrow {
      font-size: 20px;
      color: var(--tech-teal);
    }
    .group-objective {
      text-align: center;
      font-size: 14px;
      color: var(--text-secondary);
      padding: 12px;
      background: rgba(16, 185, 129, 0.08);
      border: 1px solid rgba(16, 185, 129, 0.2);
      border-radius: 8px;
    }
    .slide-5-right {
      flex: 1;
      display: flex;
      flex-direction: column;
      gap: 12px;
    }
    .slide-5-right h2 {
      font-size: 24px;
      font-weight: 800;
    }
    .kanban-board {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 10px;
      flex: 1;
    }
    .kanban-col {
      background: var(--bg-secondary);
      border: 1px solid var(--border-slate);
      border-radius: 10px;
      padding: 12px;
      display: flex;
      flex-direction: column;
      gap: 8px;
    }
    .kanban-header {
      font-size: 12px;
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: 1px;
      padding-bottom: 8px;
      border-bottom: 2px solid var(--border-slate);
      display: flex;
      align-items: center;
      gap: 6px;
    }
    .kanban-col:nth-child(1) .kanban-header { color: var(--text-muted); border-color: var(--text-muted); }
    .kanban-col:nth-child(2) .kanban-header { color: var(--tech-teal); border-color: var(--tech-teal); }
    .kanban-col:nth-child(3) .kanban-header { color: var(--success); border-color: var(--success); }
    .kanban-card {
      background: var(--bg-primary);
      border: 1px solid var(--border-slate);
      border-radius: 6px;
      padding: 10px;
      font-size: 12px;
      color: var(--text-secondary);
    }
    /* Slide 6: Mentors */
    .slide-6 {
      display: flex;
      flex-direction: column;
      gap: 16px;
    }
    .slide-6 h2 {
      font-size: 24px;
      font-weight: 800;
    }
    .guilds-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 14px;
      flex: 1;
    }
    .guild-panel {
      background: var(--bg-secondary);
      border: 1px solid var(--border-slate);
      border-radius: 12px;
      padding: 20px;
      display: flex;
      flex-direction: column;
      gap: 14px;
      transition: all 0.2s ease;
      cursor: pointer;
    }
    .guild-panel:hover {
      border-color: var(--tech-teal);
    }
    .guild-header {
      display: flex;
      align-items: center;
      gap: 12px;
    }
    .guild-avatar {
      width: 48px;
      height: 48px;
      border-radius: 50%;
      background: var(--gradient-accent);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 20px;
      font-weight: 700;
      color: white;
    }
    .guild-info h3 {
      font-size: 16px;
      font-weight: 700;
    }
    .guild-info p {
      font-size: 12px;
      color: var(--text-secondary);
    }
    .guild-focus {
      padding: 8px 12px;
      background: rgba(0, 82, 255, 0.08);
      border-radius: 8px;
      font-size: 12px;
      font-weight: 600;
    }
    .guild-ownership {
      padding: 6px 12px;
      background: rgba(16, 185, 129, 0.08);
      border: 1px solid rgba(16, 185, 129, 0.2);
      border-radius: 8px;
      font-size: 11px;
      font-weight: 600;
      color: var(--text-secondary);
      line-height: 1.4;
    }
    .ownership-label {
      color: var(--success);
      font-weight: 700;
      color: var(--tech-teal);
    }
    .mentor-responsibilities {
      display: flex;
      flex-direction: column;
      gap: 10px;
    }
    .responsibility-title {
      font-size: 14px;
      font-weight: 700;
      display: flex;
      align-items: center;
      gap: 8px;
    }
    .responsibility-list {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
    }
    .responsibility-tag {
      padding: 6px 12px;
      background: var(--bg-primary);
      border: 1px solid var(--border-slate);
      border-radius: 6px;
      font-size: 12px;
      color: var(--text-secondary);
    }
    /* Slide 7: Week 1 Schedule */
    .slide-7 {
      display: flex;
      gap: 24px;
    }
    .slide-7-left {
      width: 280px;
      display: flex;
      flex-direction: column;
      justify-content: center;
      gap: 12px;
    }
    .slide-7-left h2 {
      font-size: 24px;
      font-weight: 800;
    }
    .week-badge-large {
      font-family: 'JetBrains Mono', monospace;
      font-size: 14px;
      color: var(--text-muted);
    }
    .slide-7-right {
      flex: 1;
      display: flex;
      flex-direction: column;
      gap: 6px;
    }
    .accordion-item {
      background: var(--bg-secondary);
      border: 1px solid var(--border-slate);
      border-radius: 10px;
      overflow: hidden;
      transition: all 0.2s ease;
    }
    .accordion-item.active {
      border-color: var(--tech-teal);
    }
    .accordion-header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 10px 16px;
      cursor: pointer;
      transition: all 0.2s ease;
    }
    .accordion-header:hover {
      background: rgba(13, 148, 251, 0.05);
    }
    .accordion-day {
      display: flex;
      align-items: center;
      gap: 12px;
    }
    .day-badge {
      font-family: 'JetBrains Mono', monospace;
      font-size: 11px;
      font-weight: 600;
      padding: 4px 10px;
      border-radius: 6px;
      background: rgba(0, 82, 255, 0.15);
      color: var(--brand-blue);
    }
    .day-title {
      font-size: 14px;
      font-weight: 700;
    }
    .accordion-icon {
      font-size: 12px;
      color: var(--text-muted);
      transition: transform 0.2s ease;
    }
    .accordion-item.active .accordion-icon {
      transform: rotate(180deg);
      color: var(--tech-teal);
    }
    .accordion-body {
      max-height: 0;
      overflow: hidden;
      transition: max-height 0.3s ease;
    }
    .accordion-item.active .accordion-body {
      max-height: 200px;
    }
    .accordion-content {
      padding: 0 18px 14px 18px;
      font-size: 13px;
      color: var(--text-secondary);
      line-height: 1.5;
    }
    /* Schedule slides shared */
    .slide-schedule {
      display: flex;
      gap: 24px;
    }
    .schedule-left {
      width: 280px;
      display: flex;
      flex-direction: column;
      justify-content: center;
      gap: 12px;
    }
    .schedule-left h2 {
      font-size: 24px;
      font-weight: 800;
    }
    .schedule-right {
      flex: 1;
      display: flex;
      flex-direction: column;
      gap: 6px;
    }
    /* Slide 8: Week 2 Schedule */
    .slide-8 {
      display: flex;
      gap: 24px;
    }
    .slide-8-left {
      width: 280px;
      display: flex;
      flex-direction: column;
      justify-content: center;
      gap: 12px;
    }
    .slide-8-left h2 {
      font-size: 24px;
      font-weight: 800;
    }
    .slide-8-right {
      flex: 1;
      display: flex;
      flex-direction: column;
      gap: 8px;
    }
    .schedule-grid {
      display: grid;
      grid-template-rows: repeat(5, 1fr);
      gap: 8px;
      flex: 1;
    }
    .schedule-step {
      display: flex;
      align-items: center;
      gap: 14px;
      padding: 12px 16px;
      background: var(--bg-secondary);
      border: 1px solid var(--border-slate);
      border-radius: 10px;
      transition: all 0.2s ease;
      cursor: pointer;
    }
    .schedule-step:hover {
      border-color: var(--tech-teal);
    }
    .step-date {
      font-family: 'JetBrains Mono', monospace;
      font-size: 11px;
      font-weight: 600;
      padding: 4px 10px;
      border-radius: 6px;
      background: rgba(13, 148, 251, 0.15);
      color: var(--tech-teal);
      min-width: 90px;
      text-align: center;
    }
    .step-content h3 {
      font-size: 14px;
      font-weight: 700;
      margin-bottom: 2px;
    }
    .step-content p {
      font-size: 12px;
      color: var(--text-secondary);
    }
    /* Slide 9: Week 3 Schedule */
    .slide-9 {
      display: flex;
      gap: 24px;
    }
    .slide-9-left {
      width: 280px;
      display: flex;
      flex-direction: column;
      justify-content: center;
      gap: 12px;
    }
    .slide-9-left h2 {
      font-size: 24px;
      font-weight: 800;
    }
    .slide-9-right {
      flex: 1;
      display: flex;
      flex-direction: column;
      gap: 8px;
    }
    .milestone-flow {
      display: flex;
      flex-direction: column;
      gap: 6px;
      flex: 1;
    }
    .milestone-item {
      display: flex;
      align-items: center;
      gap: 14px;
      padding: 10px 16px;
      background: var(--bg-secondary);
      border: 1px solid var(--border-slate);
      border-radius: 10px;
      transition: all 0.2s ease;
      cursor: pointer;
    }
    .milestone-item:hover {
      border-color: var(--tech-teal);
    }
    .milestone-item.highlight {
      border-color: var(--alert);
      background: rgba(245, 158, 11, 0.08);
    }
    .milestone-date {
      font-family: 'JetBrains Mono', monospace;
      font-size: 11px;
      font-weight: 600;
      padding: 4px 10px;
      border-radius: 6px;
      background: rgba(245, 158, 11, 0.15);
      color: var(--alert);
      min-width: 90px;
      text-align: center;
    }
    .milestone-content h3 {
      font-size: 14px;
      font-weight: 700;
      margin-bottom: 2px;
    }
    .milestone-content p {
      font-size: 12px;
      color: var(--text-secondary);
    }
    /* Slide 10: A Day in Your Life */
    .slide-10 {
      display: flex;
      flex-direction: column;
      gap: 16px;
    }
    .slide-10 h2 {
      font-size: 24px;
      font-weight: 800;
    }
    .timeline-visualizer {
      display: flex;
      flex-direction: column;
      gap: 12px;
      flex: 1;
      justify-content: center;
    }
    .time-block {
      display: flex;
      align-items: stretch;
      gap: 16px;
      transition: all 0.2s ease;
    }
    .time-label {
      width: 160px;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: flex-end;
      gap: 2px;
    }
    .time-label .time {
      font-family: 'JetBrains Mono', monospace;
      font-size: 14px;
      font-weight: 600;
      color: var(--text-secondary);
    }
    .time-label .duration {
      font-size: 11px;
      color: var(--text-muted);
    }
    .time-content {
      flex: 1;
      padding: 16px 20px;
      background: var(--bg-secondary);
      border: 1px solid var(--border-slate);
      border-radius: 10px;
      display: flex;
      align-items: center;
      gap: 12px;
    }
    .time-block.highlight .time-content {
      border-color: var(--brand-blue);
      background: rgba(0, 82, 255, 0.08);
      box-shadow: 0 0 20px rgba(0, 82, 255, 0.15);
    }
    .time-icon {
      width: 36px;
      height: 36px;
      border-radius: 8px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 16px;
      background: rgba(0, 82, 255, 0.15);
      color: var(--brand-blue);
    }
    .time-block.highlight .time-icon {
      background: var(--gradient-accent);
      color: white;
    }
    .time-text h3 {
      font-size: 15px;
      font-weight: 700;
      margin-bottom: 2px;
    }
    .time-text p {
      font-size: 13px;
      color: var(--text-secondary);
    }
    /* Slide 11: Achievements */
    .slide-11 {
      display: flex;
      align-items: center;
      justify-content: center;
    }
    .roadmap-container {
      width: 660px;
      background: var(--bg-secondary);
      border: 1px solid var(--border-slate);
      border-radius: 16px;
      padding: 32px 40px;
      display: flex;
      flex-direction: column;
      gap: 20px;
      box-shadow: 0 20px 60px rgba(0, 0, 0, 0.5);
    }
    .roadmap-header {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 8px;
      text-align: center;
    }
    .roadmap-icon {
      width: 48px;
      height: 48px;
      border-radius: 50%;
      background: linear-gradient(135deg, var(--brand-blue), var(--tech-teal));
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 20px;
      color: white;
      box-shadow: 0 0 20px rgba(0, 82, 255, 0.3);
    }
    .roadmap-header h2 {
      font-size: 22px;
      font-weight: 800;
      margin-bottom: 2px;
    }
    .roadmap-subtitle {
      font-size: 13px;
      color: var(--text-muted);
      margin-top: 0;
    }
    .roadmap-timeline {
      display: flex;
      flex-direction: column;
      gap: 6px;
    }
    .roadmap-phase {
      display: flex;
      align-items: flex-start;
      gap: 14px;
      padding: 12px 14px;
      border-radius: 10px;
      transition: all 0.2s ease;
    }
    .roadmap-phase:hover {
      background: rgba(0, 82, 255, 0.03);
    }
    .roadmap-phase.phase-active {
      background: rgba(0, 82, 255, 0.08);
      border: 1px solid rgba(0, 82, 255, 0.25);
    }
    .phase-marker {
      width: 28px;
      height: 28px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 11px;
      flex-shrink: 0;
      margin-top: 2px;
    }
    .phase-past {
      background: rgba(16, 185, 129, 0.15);
      color: var(--success);
      border: 1px solid var(--success);
    }
    .phase-current {
      background: rgba(0, 82, 255, 0.2);
      color: var(--brand-blue);
      border: 1px solid var(--brand-blue);
      box-shadow: 0 0 10px rgba(0, 82, 255, 0.3);
    }
    .phase-upcoming {
      background: rgba(100, 116, 139, 0.15);
      color: var(--text-muted);
      border: 1px solid var(--border-slate);
    }
    .phase-body {
      flex: 1;
      display: flex;
      flex-direction: column;
      gap: 2px;
    }
    .phase-label {
      font-family: 'JetBrains Mono', monospace;
      font-size: 10px;
      color: var(--text-muted);
      font-weight: 600;
    }
    .phase-title {
      font-size: 14px;
      font-weight: 700;
      color: var(--text-primary);
    }
    .phase-desc {
      font-size: 12px;
      color: var(--text-secondary);
      line-height: 1.4;
    }
    .roadmap-footer {
      display: flex;
      justify-content: center;
      gap: 10px;
      flex-wrap: wrap;
      padding-top: 8px;
      border-top: 1px dashed var(--border-slate);
    }
    .roadmap-badge {
      display: inline-flex;
      align-items: center;
      gap: 5px;
      padding: 5px 12px;
      border-radius: 20px;
      font-size: 12px;
      font-weight: 600;
      background: var(--bg-primary);
      border: 1px solid var(--border-slate);
      color: var(--text-secondary);
    }
    .roadmap-badge i {
      font-size: 10px;
      color: var(--tech-teal);
    }
    /* Slide 12: Launch */
    .slide-12 {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      gap: 24px;
      text-align: center;
    }
    .slide-12 h2 {
      font-size: 36px;
      font-weight: 800;
      background: var(--gradient-text);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }
    .welcome-badge {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      padding: 8px 20px;
      background: linear-gradient(135deg, rgba(0, 82, 255, 0.15), rgba(13, 148, 251, 0.15));
      border: 1px solid rgba(0, 82, 255, 0.3);
      border-radius: 30px;
      font-size: 15px;
      font-weight: 700;
      color: var(--tech-teal);
      letter-spacing: 0.5px;
    }
    .welcome-badge i {
      color: var(--alert);
    }
    .slide-12-subtitle {
      font-size: 16px;
      color: var(--text-muted);
      margin-top: -10px;
      margin-bottom: 4px;
    }
    .date-highlight {
      font-family: 'JetBrains Mono', monospace;
      font-size: 18px;
      color: var(--tech-teal);
      font-weight: 600;
    }
    .cta-btn {
      padding: 18px 48px;
      font-size: 18px;
      font-weight: 700;
      font-family: 'JetBrains Mono', monospace;
      letter-spacing: 2px;
      background: transparent;
      border: 2px solid var(--brand-blue);
      color: var(--brand-blue);
      border-radius: 12px;
      cursor: pointer;
      transition: all 0.3s ease;
      position: relative;
      overflow: hidden;
    }
    .cta-btn:hover {
      background: var(--gradient-accent);
      color: white;
      border-color: transparent;
      box-shadow: 0 0 40px rgba(0, 82, 255, 0.4);
      transform: translateY(-2px);
    }
    .sub-note {
      font-size: 14px;
      color: var(--text-muted);
    }
    #confetti-canvas {
      position: absolute;
      top: 0;
      left: 0;
      width: 1280px;
      height: 720px;
      pointer-events: none;
      z-index: 10;
    }
    /* Background grid pattern */
    .grid-bg {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-image:
        linear-gradient(rgba(13, 148, 251, 0.03) 1px, transparent 1px),
        linear-gradient(90deg, rgba(13, 148, 251, 0.03) 1px, transparent 1px);
      background-size: 60px 60px;
      pointer-events: none;
      z-index: 0;
    }
    .slide-content {
      position: relative;
      z-index: 1;
      width: 100%;
      height: 100%;
      display: flex;
      flex-direction: column;
    }
    /* Progress bar for timeline */
    .timeline-bar {
      display: flex;
      align-items: center;
      gap: 4px;
      margin: 8px 0;
    }
    .timeline-dot {
      width: 12px;
      height: 12px;
      border-radius: 50%;
      background: var(--border-slate);
      border: 2px solid var(--border-slate);
    }
    .timeline-dot.active {
      background: var(--brand-blue);
      border-color: var(--tech-teal);
      box-shadow: 0 0 8px rgba(0, 82, 255, 0.5);
    }
    .timeline-line {
      flex: 1;
      height: 2px;
      background: var(--border-slate);
    }
    .timeline-line.active {
      background: var(--gradient-accent);
    }
    /* Week schedule generic */
    .week-schedule-slide {
      display: flex;
      gap: 24px;
    }
    .week-schedule-left {
      width: 280px;
      display: flex;
      flex-direction: column;
      justify-content: center;
      gap: 12px;
    }
    .week-schedule-left h2 {
      font-size: 24px;
      font-weight: 800;
    }
    .week-schedule-right {
      flex: 1;
      display: flex;
      flex-direction: column;
      gap: 6px;
    }
    .week-schedule-item {
      display: flex;
      align-items: center;
      gap: 14px;
      padding: 14px 16px;
      background: var(--bg-secondary);
      border: 1px solid var(--border-slate);
      border-radius: 10px;
      transition: all 0.2s ease;
      cursor: pointer;
    }
    .week-schedule-item:hover {
      border-color: var(--tech-teal);
    }
    .week-schedule-item.active {
      border-color: var(--tech-teal);
      background: rgba(13, 148, 251, 0.05);
    }
    .week-day-badge {
      font-family: 'JetBrains Mono', monospace;
      font-size: 11px;
      font-weight: 600;
      padding: 4px 10px;
      border-radius: 6px;
      background: rgba(0, 82, 255, 0.15);
      color: var(--brand-blue);
      min-width: 90px;
      text-align: center;
    }
    .week-schedule-content h3 {
      font-size: 14px;
      font-weight: 700;
      margin-bottom: 2px;
    }
    .week-schedule-content p {
      font-size: 12px;
      color: var(--text-secondary);
    }
  </style>
</head>
<body>
<div class="deck-container">
  <div class="slide-wrapper">

    <!-- Slide 1: Welcome -->
    <div class="slide-container active" id="slide1">
      <div class="grid-bg"></div>
      <div class="slide-content slide-1">
        <div class="slide-1-left">
          <div class="brand-label">
            <i class="fas fa-bolt"></i>
            Razorpay Academy
          </div>
          <h1 class="main-title gradient-text">AI BOOTCAMP<br>2026</h1>
          <div class="meta-line">
            <i class="far fa-calendar"></i>
            July 22 – August 14, 2026 | Daily 5:00 PM – 6:00 PM
          </div>
          <div class="terminal" style="margin-top: 8px;">
            <div class="terminal-header">
              <div class="terminal-dot red"></div>
              <div class="terminal-dot yellow"></div>
              <div class="terminal-dot green"></div>
              <span style="font-size: 11px; color: var(--text-muted); margin-left: 8px;">bootcamp --init</span>
            </div>
            <div class="terminal-body">
              <div><span class="cmd">$</span> <span class="highlight">bootcamp --init --track=ai-engineering</span></div>
              <div class="output">[INFO] Initializing Razorpay AI Bootcamp 2026...</div>
              <div class="output">[OK] Cohort loaded: 36 rookies (11 PPO)</div>
              <div class="output">[OK] Guilds formed: 3 project teams (8 sub-teams)</div>
              <div class="output">[OK] Project Guilds assigned to each team</div>
              <div class="output">[OK] Mentors assigned: Platform, AI, DevSecOps</div>
              <div class="success">[SUCCESS] Bootcamp environment ready. See you July 22 at 5:00 PM.</div>
            </div>
          </div>
        </div>
        <div class="slide-1-right">
          <div class="profile-widget">
            <h3>Cohort Profile</h3>
            <div class="stat-row">
              <span class="stat-label">Cohort Size</span>
              <span class="stat-value">36 Rookies</span>
            </div>
            <div class="stat-row">
              <span class="stat-label">Project Guilds</span>
              <span class="stat-value">3 Guilds</span>
            </div>
            <div class="stat-row">
              <span class="stat-label">Duration</span>
              <span class="stat-value">4 Weeks</span>
            </div>
            <div class="stat-row">
              <span class="stat-label">Daily Sync</span>
              <span class="stat-value">5:00 PM IST</span>
            </div>
          </div>
          <div class="section-title">Core <span>Outcomes</span></div>
          <div class="outcomes-list">
            <div class="outcome-item">
              <i class="fas fa-check-circle"></i>
              Build with AI
            </div>
            <div class="outcome-item">
              <i class="fas fa-check-circle"></i>
              Ship a Real Project
            </div>
            <div class="outcome-item">
              <i class="fas fa-check-circle"></i>
              Graduate Future-Ready
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Slide 2: What Is AI? -->
    <div class="slide-container" id="slide2">
      <div class="grid-bg"></div>
      <div class="slide-content slide-2">
        <div class="slide-2-header">
          <h2>What Is <span class="gradient-text">AI</span>?</h2>
          <div class="values-bar">
            <span class="value-chip"><i class="fas fa-bolt"></i> Speed</span>
            <span class="value-chip"><i class="fas fa-lightbulb"></i> Innovation</span>
            <span class="value-chip"><i class="fas fa-handshake"></i> Customer First</span>
            <span class="value-chip"><i class="fas fa-shield-halved"></i> Ownership</span>
            <span class="value-chip"><i class="fas fa-users"></i> Collaboration</span>
          </div>
        </div>
        <div class="card-grid">
          <div class="feature-card">
            <div class="feature-icon"><i class="fas fa-pen-nib"></i></div>
            <h3>Writes</h3>
            <p>Writes code & boilerplate instantaneously. From functions to full modules, AI generates syntactically correct, context-aware code.</p>
          </div>
          <div class="feature-card">
            <div class="feature-icon"><i class="fas fa-bug"></i></div>
            <h3>Debugs</h3>
            <p>Tracks down logic flaws & error leaks. AI analyzes stack traces, identifies root causes, and suggests precise fixes.</p>
          </div>
          <div class="feature-card">
            <div class="feature-icon"><i class="fas fa-chalkboard-user"></i></div>
            <h3>Teaches</h3>
            <p>Explains complex system architectures on-demand. Break down monoliths, microservices, and data flows in plain language.</p>
          </div>
          <div class="feature-card">
            <div class="feature-icon"><i class="fas fa-rocket"></i></div>
            <h3>Accelerates</h3>
            <p>Automates workflows & deployment script writing. CI/CD pipelines, infra-as-code, and test suites — generated in seconds.</p>
          </div>
        </div>
        <div class="callout-panel">
          <i class="fas fa-lightbulb"></i>
          <span>AI does not replace you; it grants you <strong>10x leverage</strong>. You remain the final decision-maker.</span>
        </div>
      </div>
    </div>

    <!-- Slide 3: Why AI Matters -->
    <div class="slide-container" id="slide3">
      <div class="grid-bg"></div>
      <div class="slide-content slide-3">
        <div class="slide-3-left">
          <h2>Why AI <span class="gradient-text">Matters</span></h2>
          <div class="benefit-tile">
            <div class="benefit-icon"><i class="fas fa-gauge-high"></i></div>
            <div class="benefit-content">
              <h3>Productivity</h3>
              <p>Automate tedious tasks and focus on systems design. Ship features in hours that once took days.</p>
            </div>
          </div>
          <div class="benefit-tile">
            <div class="benefit-icon"><i class="fas fa-medal"></i></div>
            <div class="benefit-content">
              <h3>Differentiation</h3>
              <p>Stand out in cohorts by building 3x faster. Demonstrate fluency in AI-augmented development workflows.</p>
            </div>
          </div>
          <div class="benefit-tile">
            <div class="benefit-icon"><i class="fas fa-shield-halved"></i></div>
            <div class="benefit-content">
              <h3>Future-Proofing</h3>
              <p>Mastery over LLM orchestration is a baseline developer skill. The engineers who leverage AI will define the next decade.</p>
            </div>
          </div>
          <div class="benefit-tile">
            <div class="benefit-icon"><i class="fas fa-puzzle-piece"></i></div>
            <div class="benefit-content">
              <h3>Hands-On Learning</h3>
              <p>From day one, you will use Cursor, GitHub Copilot, and Razorpay's own LLM gateway to ship production-grade code.</p>
            </div>
          </div>
        </div>
        <div class="slide-3-right">
          <div class="metrics-widget-horizontal">
            <div class="metrics-h-left">
              <div class="badge badge-brand"><i class="fas fa-chart-line"></i> Razorpay Impact</div>
              <div class="big-counter">10,000+</div>
            </div>
            <div class="metrics-h-right">
              <div class="metrics-context">
                Razorpay already implements AI workflows<br>assisting thousands of active businesses daily.<br><br>
                <span style="color: var(--text-muted);">From fraud detection to merchant onboarding,<br>AI is embedded in our production systems.</span>
              </div>
            </div>
          </div>
          <div class="ai-stack-panel">
            <div class="section-title">Razorpay <span>AI Stack</span></div>
            <div class="stack-grid">
              <div class="stack-item"><i class="fas fa-robot"></i> LLM Gateway</div>
              <div class="stack-item"><i class="fas fa-code-branch"></i> GitHub Copilot</div>
              <div class="stack-item"><i class="fas fa-terminal"></i> Cursor IDE</div>
              <div class="stack-item"><i class="fas fa-database"></i> Vector Stores</div>
              <div class="stack-item"><i class="fas fa-brain"></i> Fine-Tuned Models</div>
              <div class="stack-item"><i class="fas fa-shield-halved"></i> AI Guardrails</div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Slide 4: Bootcamp Overview -->
    <div class="slide-container" id="slide4">
      <div class="grid-bg"></div>
      <div class="slide-content slide-4">
        <h2>Program <span class="gradient-text">Architecture</span> <span style="font-size: 16px; color: var(--text-muted);">/ 4-Week Blueprint</span></h2>
        <div class="timeline-container">
          <div class="timeline-bar">
            <div class="timeline-dot active"></div>
            <div class="timeline-line active"></div>
            <div class="timeline-dot active"></div>
            <div class="timeline-line active"></div>
            <div class="timeline-dot active"></div>
            <div class="timeline-line active"></div>
            <div class="timeline-dot active"></div>
          </div>
          <div class="week-columns">
            <div class="week-card">
              <div class="week-header">
                <span class="week-number">WEEK 1</span>
                <span class="week-dates">Jul 22 – 26</span>
              </div>
              <h3>AI Foundations</h3>
              <div class="week-topics">
                <div class="week-topic"><i class="fas fa-chevron-right"></i> Tooling setup</div>
                <div class="week-topic"><i class="fas fa-chevron-right"></i> Prompting patterns</div>
                <div class="week-topic"><i class="fas fa-chevron-right"></i> IDE agents</div>
                <div class="week-topic"><i class="fas fa-chevron-right"></i> GitHub Copilot</div>
              </div>
              <div class="badge badge-brand" style="margin-top: auto; align-self: flex-start;"><i class="fas fa-graduation-cap"></i> Learn</div>
            </div>
            <div class="week-card">
              <div class="week-header">
                <span class="week-number">WEEK 2</span>
                <span class="week-dates">Jul 27 – 31</span>
              </div>
              <h3>Foundations & Infra</h3>
              <div class="week-topics">
                <div class="week-topic"><i class="fas fa-chevron-right"></i> Domain foundations</div>
                <div class="week-topic"><i class="fas fa-chevron-right"></i> Service dependencies</div>
                <div class="week-topic"><i class="fas fa-chevron-right"></i> Coding standards</div>
                <div class="week-topic"><i class="fas fa-chevron-right"></i> Schema essentials</div>
              </div>
              <div class="badge badge-success" style="margin-top: auto; align-self: flex-start;"><i class="fas fa-hammer"></i> Build</div>
            </div>
            <div class="week-card">
              <div class="week-header">
                <span class="week-number">WEEK 3</span>
                <span class="week-dates">Aug 3 – 7</span>
              </div>
              <h3>Core Ecosystem</h3>
              <div class="week-topics">
                <div class="week-topic"><i class="fas fa-chevron-right"></i> Outbound systems</div>
                <div class="week-topic"><i class="fas fa-chevron-right"></i> Ecosystem safety</div>
                <div class="week-topic"><i class="fas fa-chevron-right"></i> Testing frameworks</div>
                <div class="week-topic"><i class="fas fa-chevron-right"></i> Telemetry platforms</div>
              </div>
              <div class="badge badge-alert" style="margin-top: auto; align-self: flex-start;"><i class="fas fa-rocket"></i> Ship</div>
            </div>
            <div class="week-card">
              <div class="week-header">
                <span class="week-number">WEEK 4</span>
                <span class="week-dates">Aug 10 – 14</span>
              </div>
              <h3>Advanced Products</h3>
              <div class="week-topics">
                <div class="week-topic"><i class="fas fa-chevron-right"></i> Notification infra</div>
                <div class="week-topic"><i class="fas fa-chevron-right"></i> Automation workflows</div>
                <div class="week-topic"><i class="fas fa-chevron-right"></i> Specialized solutions</div>
                <div class="week-topic"><i class="fas fa-chevron-right"></i> Capstone demos</div>
              </div>
              <div class="badge badge-brand" style="margin-top: auto; align-self: flex-start;"><i class="fas fa-trophy"></i> Demo</div>
            </div>
          </div>
        </div>
        <div class="footer-alert">
          <i class="fas fa-clock"></i>
          <span>Anchor session: Daily at 5:00 PM. Rest of the day is structured for asynchronous project development.</span>
        </div>
      </div>
    </div>

    <!-- Slide 5: How We Work -->
    <div class="slide-container" id="slide5">
      <div class="grid-bg"></div>
      <div class="slide-content slide-5">
        <div class="slide-5-left">
          <h2>How We <span class="gradient-text">Work</span></h2>
          <div class="group-card">
            <div class="section-title">Group <span>Allocation</span></div>
            <div class="group-flow">
              <div class="group-block">
                <div class="number">36</div>
                <div class="label">Rookies</div>
              </div>
              <i class="fas fa-arrow-right group-arrow"></i>
              <div class="group-block">
                <div class="number">8</div>
                <div class="label">Teams</div>
              </div>
              <i class="fas fa-arrow-right group-arrow"></i>
              <div class="group-block">
                <div class="number">4-5</div>
                <div class="label">Per Team</div>
              </div>
            </div>
            <div class="group-objective">
              <i class="fas fa-bullseye" style="margin-right: 6px;"></i>
              Collaborate to construct and deploy <strong>1 production-ready project</strong>
            </div>
          </div>
        </div>
        <div class="slide-5-right">
          <h2 style="font-size: 20px;">Project <span class="gradient-text">Kanban</span></h2>
          <div class="kanban-board">
            <div class="kanban-col">
              <div class="kanban-header"><i class="fas fa-circle" style="font-size: 8px;"></i> Backlog</div>
              <div class="kanban-card">Ideate project scope</div>
              <div class="kanban-card">Define MVP features</div>
              <div class="kanban-card">Assign guild roles</div>
              <div class="kanban-card">Set up repositories</div>
            </div>
            <div class="kanban-col">
              <div class="kanban-header"><i class="fas fa-circle" style="font-size: 8px;"></i> Doing</div>
              <div class="kanban-card">Daily 5 PM Check-ins</div>
              <div class="kanban-card">Code sprints</div>
              <div class="kanban-card">AI pair programming</div>
              <div class="kanban-card">Mentor reviews</div>
            </div>
            <div class="kanban-col">
              <div class="kanban-header"><i class="fas fa-circle" style="font-size: 8px;"></i> Done</div>
              <div class="kanban-card">Merge to Main</div>
              <div class="kanban-card">Deploy to staging</div>
              <div class="kanban-card">Security audit pass</div>
              <div class="kanban-card">Demo Day ready</div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Slide 6: Mentors & Buddies -->
    <div class="slide-container" id="slide6">
      <div class="grid-bg"></div>
      <div class="slide-content slide-6">
        <div>
          <h2 style="margin-bottom: 4px;">Your <span class="gradient-text">Mentors</span> & Buddies</h2>
          <div style="display: flex; align-items: center; gap: 8px; flex-wrap: wrap;">
            <span class="badge badge-success"><i class="fas fa-user-group"></i> 1 Mentor / Buddy Per Group</span>
            <span class="badge badge-brand"><i class="fas fa-rocket"></i> Project Assigned on Date of Joining</span>
          </div>
        </div>
        <div class="guilds-grid">
          <div class="guild-panel">
            <div class="guild-header">
              <div class="guild-avatar"><i class="fas fa-microchip"></i></div>
              <div class="guild-info">
                <h3>Platform Guild Mentor</h3>
                <p>Lead Platform Architect</p>
              </div>
            </div>
            <div class="badge badge-brand">Guild 1</div>
            <div class="guild-focus">
              <i class="fas fa-microchip" style="margin-right: 6px;"></i>
              Focus: Performance & System Design
            </div>
            <div class="guild-ownership">
              <i class="fas fa-crown" style="margin-right: 5px; color: var(--tech-teal);"></i>
              <span class="ownership-label">Ownership:</span> System design, infra architecture, code quality reviews for 3 teams
            </div>
            <div class="terminal">
              <div class="terminal-body" style="font-size: 11px;">
                <div><span class="cmd">$</span> <span class="highlight">mentor --info</span></div>
                <div class="output">role: platform_architect</div>
                <div class="output">expertise: ["scalability", "infra"]</div>
                <div class="success">teams: 3 | status: available</div>
              </div>
            </div>
          </div>
          <div class="guild-panel">
            <div class="guild-header">
              <div class="guild-avatar" style="background: linear-gradient(135deg, #10B981 0%, #0D94FB 100%);"><i class="fas fa-brain"></i></div>
              <div class="guild-info">
                <h3>AI Guild Mentor</h3>
                <p>Senior AI Engineer</p>
              </div>
            </div>
            <div class="badge badge-success">Guild 2</div>
            <div class="guild-focus">
              <i class="fas fa-brain" style="margin-right: 6px;"></i>
              Focus: Prompt Engineering & Model Fine-Tuning
            </div>
            <div class="guild-ownership">
              <i class="fas fa-crown" style="margin-right: 5px; color: var(--tech-teal);"></i>
              <span class="ownership-label">Ownership:</span> LLM integration, prompt tuning, AI tooling enablement for 3 teams
            </div>
            <div class="terminal">
              <div class="terminal-body" style="font-size: 11px;">
                <div><span class="cmd">$</span> <span class="highlight">mentor --info</span></div>
                <div class="output">role: ai_engineer</div>
                <div class="output">expertise: ["llms", "fine-tuning"]</div>
                <div class="success">teams: 3 | status: available</div>
              </div>
            </div>
          </div>
          <div class="guild-panel">
            <div class="guild-header">
              <div class="guild-avatar" style="background: linear-gradient(135deg, #F59E0B 0%, #EF4444 100%);"><i class="fas fa-shield-halved"></i></div>
              <div class="guild-info">
                <h3>DevSecOps Guild Mentor</h3>
                <p>Principal DevSecOps</p>
              </div>
            </div>
            <div class="badge badge-alert">Guild 3</div>
            <div class="guild-focus">
              <i class="fas fa-shield-halved" style="margin-right: 6px;"></i>
              Focus: APIs, Scaling, & Safe Pipelines
            </div>
            <div class="guild-ownership">
              <i class="fas fa-crown" style="margin-right: 5px; color: var(--tech-teal);"></i>
              <span class="ownership-label">Ownership:</span> Security guardrails, CI/CD pipelines, deployment orchestration for 2 teams
            </div>
            <div class="terminal">
              <div class="terminal-body" style="font-size: 11px;">
                <div><span class="cmd">$</span> <span class="highlight">mentor --info</span></div>
                <div class="output">role: devsecops</div>
                <div class="output">expertise: ["security", "pipelines"]</div>
                <div class="success">teams: 2 | status: available</div>
              </div>
            </div>
          </div>
        </div>
        <div class="mentor-responsibilities">
          <div class="responsibility-title">
            <i class="fas fa-list-check" style="color: var(--tech-teal);"></i>
            Shared Mentor Responsibilities
          </div>
          <div class="responsibility-list">
            <span class="responsibility-tag"><i class="fas fa-code" style="margin-right: 4px;"></i>Code reviews</span>
            <span class="responsibility-tag"><i class="fas fa-unlock" style="margin-right: 4px;"></i>Architectural unblocking</span>
            <span class="responsibility-tag"><i class="fas fa-clipboard-check" style="margin-right: 4px;"></i>Daily checkpoint checks</span>
            <span class="responsibility-tag"><i class="fas fa-users" style="margin-right: 4px;"></i>1:1 guidance sessions</span>
            <span class="responsibility-tag"><i class="fas fa-rocket" style="margin-right: 4px;"></i>Deploy support</span>
          </div>
        </div>
      </div>
    </div>

    <!-- Slide 7: Week 1 Schedule -->
    <div class="slide-container" id="slide7">
      <div class="grid-bg"></div>
      <div class="slide-content slide-7">
        <div class="slide-7-left">
          <h2>Week 1</h2>
          <div class="week-badge-large">AI Foundations<br>July 22 – July 26</div>
          <div class="terminal" style="margin-top: 8px;">
            <div class="terminal-header">
              <div class="terminal-dot red"></div>
              <div class="terminal-dot yellow"></div>
              <div class="terminal-dot green"></div>
            </div>
            <div class="terminal-body">
              <div><span class="cmd">$</span> <span class="highlight">schedule --week=1</span></div>
              <div class="output">theme: ai_foundations</div>
              <div class="output">focus: tooling + prompts</div>
              <div class="success">5 bootcamp sessions planned</div>
            </div>
          </div>
        </div>
        <div class="slide-7-right">
          <div class="accordion-item">
            <div class="accordion-header" onclick="toggleAccordion(this)">
              <div class="accordion-day">
                <span class="day-badge">Mon Jul 22</span>
                <span class="day-title">Bootcamp Kickoff</span>
              </div>
              <i class="fas fa-chevron-down accordion-icon"></i>
            </div>
            <div class="accordion-body">
              <div class="accordion-content">
                The AI Bootcamp begins! Meet your guild, set up development environments, and get hands-on with GitHub Copilot and Cursor IDE. Install extensions, configure AI assistants, and run your first AI-assisted code generation.
              </div>
            </div>
          </div>
          <div class="accordion-item">
            <div class="accordion-header" onclick="toggleAccordion(this)">
              <div class="accordion-day">
                <span class="day-badge">Tue Jul 23</span>
                <span class="day-title">Prompt Engineering</span>
              </div>
              <i class="fas fa-chevron-down accordion-icon"></i>
            </div>
            <div class="accordion-body">
              <div class="accordion-content">
                Crafting robust prompt chains. Learn zero-shot, few-shot, and chain-of-thought prompting. Build reusable prompt templates for code generation, debugging, and documentation.
              </div>
            </div>
          </div>
          <div class="accordion-item active">
            <div class="accordion-header" onclick="toggleAccordion(this)">
              <div class="accordion-day">
                <span class="day-badge">Wed Jul 24</span>
                <span class="day-title">AI-Assisted Coding</span>
              </div>
              <i class="fas fa-chevron-down accordion-icon"></i>
            </div>
            <div class="accordion-body">
              <div class="accordion-content">
                Pair programming techniques with AI. Learn to iterate on AI-generated code, review suggestions critically, and maintain code quality while moving fast.
              </div>
            </div>
          </div>
          <div class="accordion-item">
            <div class="accordion-header" onclick="toggleAccordion(this)">
              <div class="accordion-day">
                <span class="day-badge">Thu Jul 25</span>
                <span class="day-title">Search & Retrieval</span>
              </div>
              <i class="fas fa-chevron-down accordion-icon"></i>
            </div>
            <div class="accordion-body">
              <div class="accordion-content">
                Navigating codebases with AI agents. Use semantic search, code embeddings, and RAG techniques to understand large projects and legacy systems efficiently.
              </div>
            </div>
          </div>
          <div class="accordion-item">
            <div class="accordion-header" onclick="toggleAccordion(this)">
              <div class="accordion-day">
                <span class="day-badge">Fri Jul 26</span>
                <span class="day-title">Mini-Demo Sprint</span>
              </div>
              <i class="fas fa-chevron-down accordion-icon"></i>
            </div>
            <div class="accordion-body">
              <div class="accordion-content">
                First-week check-in with mentors. Present your tooling setup, demonstrate prompt techniques, and receive feedback on your AI workflow optimization.
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Slide 8: Week 2 Schedule -->
    <div class="slide-container" id="slide8">
      <div class="grid-bg"></div>
      <div class="slide-content week-schedule-slide">
        <div class="week-schedule-left">
          <h2>Week 2</h2>
          <div class="week-badge-large">Foundations & Infra<br>July 27 – July 31</div>
          <div class="terminal" style="margin-top: 8px;">
            <div class="terminal-header">
              <div class="terminal-dot red"></div>
              <div class="terminal-dot yellow"></div>
              <div class="terminal-dot green"></div>
            </div>
            <div class="terminal-body">
              <div><span class="cmd">$</span> <span class="highlight">schedule --week=2</span></div>
              <div class="output">theme: foundations_infra</div>
              <div class="output">focus: domains + services</div>
              <div class="success">5 bootcamp sessions planned</div>
            </div>
          </div>
        </div>
        <div class="week-schedule-right">
          <div class="week-schedule-item active">
            <span class="week-day-badge">Mon Jul 27</span>
            <div class="week-schedule-content">
              <h3>Domain Foundations & Lifecycles</h3>
              <p>Understanding core business domains, entity lifecycles, and the Razorpay ecosystem map.</p>
            </div>
          </div>
          <div class="week-schedule-item">
            <span class="week-day-badge">Tue Jul 28</span>
            <div class="week-schedule-content">
              <h3>Technical Request Path & Service Dependencies</h3>
              <p>Tracing a request through the system, service mesh topology, and dependency mapping.</p>
            </div>
          </div>
          <div class="week-schedule-item">
            <span class="week-day-badge">Wed Jul 29</span>
            <div class="week-schedule-content">
              <h3>Language Core & Coding Standards</h3>
              <p>Language fundamentals, style guides, linting, and writing idiomatic, maintainable code.</p>
            </div>
          </div>
          <div class="week-schedule-item">
            <span class="week-day-badge">Thu Jul 30</span>
            <div class="week-schedule-content">
              <h3>Local Infrastructure & Integration Mechanics</h3>
              <p>Local dev environments, Docker, service wiring, and integration testing fundamentals.</p>
            </div>
          </div>
          <div class="week-schedule-item">
            <span class="week-day-badge">Fri Jul 31</span>
            <div class="week-schedule-content">
              <h3>Schema & Messaging Essentials</h3>
              <p>Data schemas, message queues, event-driven patterns, and contract-first design.</p>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Slide 9: Week 3 Schedule -->
    <div class="slide-container" id="slide9">
      <div class="grid-bg"></div>
      <div class="slide-content week-schedule-slide">
        <div class="week-schedule-left">
          <h2>Week 3</h2>
          <div class="week-badge-large">Core Ecosystem<br>August 3 – August 7</div>
          <div class="terminal" style="margin-top: 8px;">
            <div class="terminal-header">
              <div class="terminal-dot red"></div>
              <div class="terminal-dot yellow"></div>
              <div class="terminal-dot green"></div>
            </div>
            <div class="terminal-body">
              <div><span class="cmd">$</span> <span class="highlight">schedule --week=3</span></div>
              <div class="output">theme: core_ecosystem</div>
              <div class="output">focus: reliability + safety</div>
              <div class="success">5 bootcamp sessions planned</div>
            </div>
          </div>
        </div>
        <div class="week-schedule-right">
          <div class="week-schedule-item active">
            <span class="week-day-badge">Mon Aug 3</span>
            <div class="week-schedule-content">
              <h3>Outbound Systems & Dispute Engines</h3>
              <p>Notification pipelines, dispute resolution workflows, and asynchronous processing patterns.</p>
            </div>
          </div>
          <div class="week-schedule-item">
            <span class="week-day-badge">Tue Aug 4</span>
            <div class="week-schedule-content">
              <h3>Forex & Ecosystem Safety</h3>
              <p>Cross-border payment flows, currency conversion, fraud signals, and risk guardrails.</p>
            </div>
          </div>
          <div class="week-schedule-item">
            <span class="week-day-badge">Wed Aug 5</span>
            <div class="week-schedule-content">
              <h3>Verification Frameworks & Testing</h3>
              <p>Unit and integration testing strategies, test pyramid, mocking, and verification automation.</p>
            </div>
          </div>
          <div class="week-schedule-item">
            <span class="week-day-badge">Thu Aug 6</span>
            <div class="week-schedule-content">
              <h3>Reliability, Alerts & Incident Response</h3>
              <p>SLOs, SLIs, alerting thresholds, on-call runbooks, and incident management workflows.</p>
            </div>
          </div>
          <div class="week-schedule-item">
            <span class="week-day-badge">Fri Aug 7</span>
            <div class="week-schedule-content">
              <h3>Data Analytics & Telemetry Platforms</h3>
              <p>Metrics collection, distributed tracing, logging strategies, and observability dashboards.</p>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Slide 10: Week 4 Schedule -->
    <div class="slide-container" id="slide10">
      <div class="grid-bg"></div>
      <div class="slide-content week-schedule-slide">
        <div class="week-schedule-left">
          <h2>Week 4</h2>
          <div class="week-badge-large">Advanced Products<br>August 10 – August 14</div>
          <div class="terminal" style="margin-top: 8px;">
            <div class="terminal-header">
              <div class="terminal-dot red"></div>
              <div class="terminal-dot yellow"></div>
              <div class="terminal-dot green"></div>
            </div>
            <div class="terminal-body">
              <div><span class="cmd">$</span> <span class="highlight">schedule --week=4</span></div>
              <div class="output">theme: advanced_products</div>
              <div class="output">focus: capstone + demo</div>
              <div class="success">5 bootcamp sessions planned</div>
            </div>
          </div>
        </div>
        <div class="week-schedule-right">
          <div class="week-schedule-item active">
            <span class="week-day-badge">Mon Aug 10</span>
            <div class="week-schedule-content">
              <h3>Engagement & Notification Infrastructure</h3>
              <p>Customer communication layers, multi-channel delivery, and engagement orchestration.</p>
            </div>
          </div>
          <div class="week-schedule-item">
            <span class="week-day-badge">Tue Aug 11</span>
            <div class="week-schedule-content">
              <h3>Intelligent Automation & Workflows</h3>
              <p>Rule engines, workflow automation, decision trees, and AI-driven business process optimization.</p>
            </div>
          </div>
          <div class="week-schedule-item">
            <span class="week-day-badge">Wed Aug 12</span>
            <div class="week-schedule-content">
              <h3>Financial Settlement & Reconciliation</h3>
              <p>Settlement cycles, ledger management, reconciliation pipelines, and financial accuracy.</p>
            </div>
          </div>
          <div class="week-schedule-item">
            <span class="week-day-badge">Thu Aug 13</span>
            <div class="week-schedule-content">
              <h3>Specialized Product Solutions</h3>
              <p>Deep dives into Razorpay's specialized product offerings and advanced feature sets.</p>
            </div>
          </div>
          <div class="week-schedule-item">
            <span class="week-day-badge" style="background: rgba(245, 158, 11, 0.15); color: var(--alert);">Fri Aug 14</span>
            <div class="week-schedule-content">
              <h3>Final Capstone Presentations</h3>
              <p>Demo Day — pitch your project to leadership, showcase your build, and celebrate graduation.</p>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Slide 11: A Day in Your Life -->
    <div class="slide-container" id="slide11">
      <div class="grid-bg"></div>
      <div class="slide-content slide-10">
        <h2>A Day in Your <span class="gradient-text">Life</span></h2>
        <div class="timeline-visualizer">
          <div class="time-block">
            <div class="time-label">
              <span class="time">10:00 AM</span>
              <span class="duration">3 hours</span>
            </div>
            <div class="time-content">
              <div class="time-icon"><i class="fas fa-users"></i></div>
              <div class="time-text">
                <h3>Collaborative Guild Huddle</h3>
                <p>Asynchronous group workspace — standups, pair programming, and guild coordination</p>
              </div>
            </div>
          </div>
          <div class="time-block">
            <div class="time-label">
              <span class="time">1:00 PM</span>
              <span class="duration">4 hours</span>
            </div>
            <div class="time-content">
              <div class="time-icon"><i class="fas fa-laptop-code"></i></div>
              <div class="time-text">
                <h3>Deep Work</h3>
                <p>Model tweaking, feature development, and unblocking sessions</p>
              </div>
            </div>
          </div>
          <div class="time-block highlight">
            <div class="time-label">
              <span class="time">5:00 PM</span>
              <span class="duration">1 hour</span>
            </div>
            <div class="time-content">
              <div class="time-icon"><i class="fas fa-graduation-cap"></i></div>
              <div class="time-text">
                <h3>AI Bootcamp Core Sync</h3>
                <p>Theory, guest speakers, live demos, and mentor check-ins</p>
              </div>
            </div>
          </div>
          <div class="time-block">
            <div class="time-label">
              <span class="time">6:00 PM</span>
              <span class="duration">onwards</span>
            </div>
            <div class="time-content">
              <div class="time-icon"><i class="fas fa-rocket"></i></div>
              <div class="time-text">
                <h3>Deploy & Review</h3>
                <p>Deploy branch, update checklist, and prepare for tomorrow</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Slide 12: Bootcamp Journey Roadmap -->
    <div class="slide-container" id="slide12">
      <div class="grid-bg"></div>
      <div class="slide-content slide-11">
        <div class="roadmap-container">
          <div class="roadmap-header">
            <div class="roadmap-icon">
              <i class="fas fa-route"></i>
            </div>
            <h2>Your <span class="gradient-text">AI Bootcamp</span> Journey</h2>
            <p class="roadmap-subtitle">From Onboarding to Demo Day — Your Roadmap Ahead</p>
          </div>
          <div class="roadmap-timeline">
            <div class="roadmap-phase">
              <div class="phase-marker phase-past"><i class="fas fa-check"></i></div>
              <div class="phase-body">
                <div class="phase-label">Jul 20</div>
                <div class="phase-title">Welcome Onboard</div>
                <div class="phase-desc">Join Razorpay, get your laptop, and meet your cohort</div>
              </div>
            </div>
            <div class="roadmap-phase">
              <div class="phase-marker phase-past"><i class="fas fa-check"></i></div>
              <div class="phase-body">
                <div class="phase-label">Jul 21</div>
                <div class="phase-title">Leadership AMA</div>
                <div class="phase-desc">Meet leaders and seniors. Get the bootcamp brief</div>
              </div>
            </div>
            <div class="roadmap-phase phase-active">
              <div class="phase-marker phase-current"><i class="fas fa-play"></i></div>
              <div class="phase-body">
                <div class="phase-label">Jul 22 – 26</div>
                <div class="phase-title">Week 1: AI Foundations</div>
                <div class="phase-desc">Tooling, prompt engineering, AI-assisted coding, and your first mini-demo</div>
              </div>
            </div>
            <div class="roadmap-phase">
              <div class="phase-marker phase-upcoming"><i class="fas fa-code"></i></div>
              <div class="phase-body">
                <div class="phase-label">Jul 27 – 31</div>
                <div class="phase-title">Week 2: Foundations & Infra</div>
                <div class="phase-desc">Domain foundations, service dependencies, coding standards, and schema essentials</div>
              </div>
            </div>
            <div class="roadmap-phase">
              <div class="phase-marker phase-upcoming"><i class="fas fa-shield-halved"></i></div>
              <div class="phase-body">
                <div class="phase-label">Aug 3 – 7</div>
                <div class="phase-title">Week 3: Core Ecosystem</div>
                <div class="phase-desc">Outbound systems, ecosystem safety, testing, and telemetry</div>
              </div>
            </div>
            <div class="roadmap-phase">
              <div class="phase-marker phase-upcoming"><i class="fas fa-rocket"></i></div>
              <div class="phase-body">
                <div class="phase-label">Aug 10 – 14</div>
                <div class="phase-title">Week 4: Advanced Products</div>
                <div class="phase-desc">Notification infra, automation workflows, specialized solutions, and Capstone Demo Day</div>
              </div>
            </div>
          </div>
          <div class="roadmap-footer">
            <span class="roadmap-badge"><i class="fas fa-users"></i> 8 Teams</span>
            <span class="roadmap-badge"><i class="fas fa-calendar"></i> 4 Weeks</span>
            <span class="roadmap-badge"><i class="fas fa-trophy"></i> 1 Demo Day</span>
            <span class="roadmap-badge"><i class="fas fa-infinity"></i> Lifelong Friends</span>
          </div>
        </div>
      </div>
    </div>

    <!-- Slide 13: Launch -->
    <div class="slide-container" id="slide13">
      <div class="grid-bg"></div>
      <canvas id="confetti-canvas"></canvas>
      <div class="slide-content slide-12">
        <div class="welcome-badge"><i class="fas fa-star"></i> Welcome to Razorpay</div>
        <h2>The Future of Payments is Built <span class="gradient-text">with AI</span></h2>
        <p class="slide-12-subtitle">AI Bootcamp 2026 — Your journey begins now</p>
        <div class="date-highlight">July 22 – August 14, 2026</div>
        <button class="cta-btn" onclick="launchConfetti()">
          <i class="fas fa-rocket" style="margin-right: 8px;"></i>[ I AM READY ]
        </button>
        <div class="sub-note">
          <i class="far fa-clock" style="margin-right: 4px;"></i>
          See you on Day 1 at 5:00 PM sharp
        </div>
      </div>
    </div>

  </div>
</div>

<!-- Navigation -->
<div class="slide-counter">01 / 13</div>
<div class="nav-controls">
  <button class="nav-btn" onclick="prevSlide()" title="Previous"><i class="fas fa-chevron-left"></i></button>
  <button class="nav-btn" onclick="nextSlide()" title="Next"><i class="fas fa-chevron-right"></i></button>
</div>

<script>
  // Slide navigation
  let currentSlide = 1;
  const totalSlides = 13;
  function showSlide(n) {
    const slides = document.querySelectorAll('.slide-container');
    if (n < 1) currentSlide = totalSlides;
    if (n > totalSlides) currentSlide = 1;
    slides.forEach((slide, index) => {
      slide.classList.remove('active');
      if (index + 1 === currentSlide) {
        slide.classList.add('active');
      }
    });
    document.querySelector('.slide-counter').textContent =
      String(currentSlide).padStart(2, '0') + ' / ' + totalSlides;
    // Auto-trigger confetti on slide 13
    if (currentSlide === 13) {
      setTimeout(launchConfetti, 400);
    }
  }
  function nextSlide() {
    currentSlide++;
    showSlide(currentSlide);
  }
  function prevSlide() {
    currentSlide--;
    showSlide(currentSlide);
  }
  // Keyboard navigation
  document.addEventListener('keydown', (e) => {
    if (e.key === 'ArrowRight' || e.key === ' ') {
      e.preventDefault();
      nextSlide();
    } else if (e.key === 'ArrowLeft') {
      e.preventDefault();
      prevSlide();
    }
  });
  // Accordion toggle
  function toggleAccordion(header) {
    const item = header.parentElement;
    const allItems = document.querySelectorAll('.accordion-item');
    allItems.forEach((acc) => {
      if (acc !== item) acc.classList.remove('active');
    });
    item.classList.toggle('active');
  }
  // Confetti effect
  function launchConfetti() {
    const canvas = document.getElementById('confetti-canvas');
    const ctx = canvas.getContext('2d');
    canvas.width = 1280;
    canvas.height = 720;
    const particles = [];
    const colors = ['#0052FF', '#0D94FB', '#10B981', '#F59E0B', '#EF4444', '#8B5CF6'];
    for (let i = 0; i < 150; i++) {
      particles.push({
        x: canvas.width / 2,
        y: canvas.height / 2,
        vx: (Math.random() - 0.5) * 12,
        vy: (Math.random() - 0.5) * 12 - 4,
        size: Math.random() * 6 + 3,
        color: colors[Math.floor(Math.random() * colors.length)],
        rotation: Math.random() * 360,
        rotationSpeed: (Math.random() - 0.5) * 10,
        opacity: 1,
        gravity: 0.15
      });
    }
    let animationId;
    function animate() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      let activeParticles = 0;
      particles.forEach((p) => {
        if (p.opacity <= 0) return;
        activeParticles++;
        p.x += p.vx;
        p.y += p.vy;
        p.vy += p.gravity;
        p.rotation += p.rotationSpeed;
        p.opacity -= 0.008;
        ctx.save();
        ctx.translate(p.x, p.y);
        ctx.rotate((p.rotation * Math.PI) / 180);
        ctx.globalAlpha = Math.max(0, p.opacity);
        ctx.fillStyle = p.color;
        ctx.fillRect(-p.size / 2, -p.size / 2, p.size, p.size);
        ctx.restore();
      });
      if (activeParticles > 0) {
        animationId = requestAnimationFrame(animate);
      } else {
        ctx.clearRect(0, 0, canvas.width, canvas.height);
      }
    }
    if (animationId) cancelAnimationFrame(animationId);
    animate();
  }
  // Initialize
  showSlide(1);
</script>
</body>
</html>
