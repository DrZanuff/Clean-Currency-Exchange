<div class='body'>
    <div class="spinner"></div>
</div>


<style>
    .body {
        background-color: #dff9fb00;
        display: flex;
        align-items: center;
        justify-content: center;
        height: 100vh;
    }
    @keyframes spin {
        to { transform: rotate(360deg);}
    }
    .spinner {
        border: 8px solid rgba(0, 0, 0, 0.1);
        border-left-color: #22a6b3;
        border-radius: 50%;
        width: 50px;
        height: 50px;
        animation: spin 1.2s linear infinite;
    }
</style>