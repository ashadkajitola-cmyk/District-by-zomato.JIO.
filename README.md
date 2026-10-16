<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cricket Schedule & PhonePe Payment Platform Pro</title>
    <style>
        :root {
            --primary: #1e3c72;
            --secondary: #2a5298;
            --phonepe: #5f259f;
            --accent: #ff9800;
            --bg: #f0f4f8;
            --white: #ffffff;
            --text: #222222;
            --danger: #e74c3c;
            --success: #2ecc71;
            --border: #dcdcdc;
        }
        * { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Segoe UI', Roboto, sans-serif; }
        body { background-color: var(--bg); color: var(--text); padding-bottom: 60px; font-size: 16px; }
        
        header { background: linear-gradient(135deg, var(--primary), var(--secondary)); color: var(--white); padding: 18px 25px; display: flex; justify-content: space-between; align-items: center; box-shadow: 0 4px 20px rgba(0,0,0,0.2); }
        header h1 { font-size: 1.4rem; font-weight: 800; }
        .user-info { display: flex; gap: 12px; align-items: center; }
        .wallet-badge { background: var(--accent); color: #000; padding: 6px 14px; border-radius: 20px; font-weight: bold; font-size: 0.95rem; text-align: center; }
        
        .container { max-width: 950px; margin: 20px auto; padding: 0 15px; display: flex; flex-direction: column; gap: 20px; }
        .card { background: var(--white); border-radius: 14px; padding: 22px; box-shadow: 0 4px 15px rgba(0,0,0,0.05); }
        
        h2 { font-size: 1.4rem; margin-bottom: 12px; color: var(--primary); font-weight: 700; }
        h3 { font-size: 1.2rem; margin-bottom: 10px; color: #333; font-weight: 700; }
        
        .btn { background: var(--secondary); color: var(--white); border: none; padding: 12px 18px; border-radius: 8px; cursor: pointer; font-weight: bold; font-size: 1rem; transition: 0.2s; width: 100%; text-align: center; display: inline-block; }
        .btn:hover { opacity: 0.92; transform: translateY(-1px); }
        .btn-phonepe { background: var(--phonepe); color: #fff; }
        .btn-danger { background: var(--danger); }
        .btn-success { background: var(--success); }
        .btn-warning { background: var(--accent); color: #000; }
        
        input, select, textarea { width: 100%; padding: 12px 15px; margin: 6px 0 16px 0; border: 2px solid var(--border); border-radius: 8px; font-size: 1rem; background: #fff; }
        input:focus, select:focus { border-color: var(--phonepe); outline: none; }
        label { font-weight: 700; font-size: 0.9rem; color: #444; display: block; }
        
        .tabs { display: flex; gap: 8px; margin-bottom: 15px; background: #e2e8f0; padding: 6px; border-radius: 10px; flex-wrap: wrap; }
        .tab-btn { flex: 1; min-width: 100px; padding: 10px; background: transparent; border: none; border-radius: 8px; cursor: pointer; font-weight: bold; color: #555; transition: 0.2s; text-align: center; }
        .tab-btn.active { background: var(--white); color: var(--phonepe); box-shadow: 0 2px 6px rgba(0,0,0,0.1); }
        
        .match-card { border: 2px solid var(--border); border-radius: 12px; padding: 18px; margin-bottom: 15px; background: var(--white); }
        .series-title-bar { background: #e8f4fd; color: #1a5276; padding: 8px 12px; border-radius: 6px; font-weight: bold; margin-bottom: 12px; display: flex; justify-content: space-between; align-items: center; }
        .match-row { display: flex; justify-content: space-between; align-items: center; margin: 12px 0; }
        .team-box { font-size: 1.15rem; font-weight: 800; color: var(--primary); }

        /* Bank UI Grid Styles */
        .popular-banks-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 15px; margin-top: 15px; }
        .bank-item { background: #fff; border: 1px solid #e0e0e0; border-radius: 12px; padding: 15px 10px; text-align: center; cursor: pointer; transition: 0.2s; display: flex; flex-direction: column; align-items: center; gap:

