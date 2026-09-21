[site_publico_seguro.html](https://github.com/user-attachments/files/32481653/site_publico_seguro.html)<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Meus Livros — Rafick Santos</title>
<link rel="icon" href="data:,">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Lora:ital,wght@0,400;0,600;1,400&family=Inter:wght@300;400;500;600&display=swap" rel="stylesheet">
<style id="app-style">
  :root {
    --bg: #FAFAFA;
    --paper: #FFFFFF;
    --border: #E5E5E5;
    --ink: #171717;
    --ink-muted: #737373;
    --accent: #262626;
    --accent-hover: #000000;
    --danger: #DC2626;
    --radius: 8px;
    color-scheme: light dark;
  }

  @media (prefers-color-scheme: dark) {
    :root {
      --bg: #0A0A0A;
      --paper: #121212;
      --border: #262626;
      --ink: #EDEEEE;
      --ink-muted: #A3A3A3;
      --accent: #E5E5E5;
      --accent-hover: #FFFFFF;
      --danger: #EF4444;
    }
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }
  body {
    font-family: 'Inter', system-ui, -apple-system, sans-serif;
    background: var(--bg);
    color: var(--ink);
    line-height: 1.6;
    padding: 0 20px;
    min-height: 100vh;
  }

  a { color: inherit; text-decoration: none; }

  #root {
    max-width: 760px;
    margin: 0 auto;
    padding: 40px 0 80px;
  }

  /* Toolbar superior */
  .top-bar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 40px;
    padding-bottom: 16px;
    border-bottom: 1px solid var(--border);
  }
  
  /* Botão visível de sair do modo autor */
  .mode-toggle {
    background: transparent;
    border: 1px solid var(--danger);
    color: var(--danger);
    padding: 6px 12px;
    border-radius: 20px;
    font-size: 13px;
    cursor: pointer;
    transition: all 0.2s ease;
  }
  .mode-toggle:hover { background: rgba(220, 38, 38, 0.1); }

  /* Botão fantasma/invisível para entrar no modo autor */
  .secret-trigger {
    background: transparent;
    border: none;
    width: 40px;
    height: 40px;
    cursor: default; /* Não mostra a mãozinha para não dar pistas */
    outline: none;
  }

  /* Hero / Perfil */
  header.hero { margin-bottom: 48px; }
  header.hero h1 { font-family: 'Lora', serif; font-size: 32px; font-weight: 600; letter-spacing: -0.5px; }
  header.hero .tagline { font-size: 15px; color: var(--ink-muted); margin-top: 4px; }
  header.hero .bio { font-size: 15px; color: var(--ink-muted); margin-top: 16px; max-width: 60ch; }

  /* Seções */
  section { margin-top: 48px; }
  .section-head {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
  }
  .section-head h2 { font-family: 'Lora', serif; font-size: 22px; font-weight: 600; }

  /* Botões */
  .btn {
    font-size: 13px;
    font-weight: 500;
    padding: 8px 14px;
    border-radius: var(--radius);
    border: 1px solid var(--border);
    background: var(--paper);
    color: var(--ink);
    cursor: pointer;
    transition: all 0.2s;
    display: inline-flex;
    align-items: center;
    gap: 6px;
  }
  .btn:hover { border-color: var(--ink-muted); background: var(--bg); }
  .btn.primary { background: var(--ink); color: var(--bg); border: none; }
  .btn.primary:hover { opacity: 0.9; }
  .btn.danger { color: var(--danger); border-color: transparent; }
  .btn.danger:hover { background: rgba(220, 38, 38, 0.08); }
  .btn.small { padding: 4px 8px; font-size: 12px; }

  /* Grid de Livros */
  .shelf {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
    gap: 24px;
  }
  .book-card { display: flex; flex-direction: column; gap: 8px; cursor: pointer; }
  .cover {
    aspect-ratio: 2 / 3;
    border-radius: var(--radius);
    background: var(--paper);
    border: 1px solid var(--border);
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
    transition: transform 0.2s ease, box-shadow 0.2s ease;
  }
  .book-card:hover .cover { transform: translateY(-2px); box-shadow: 0 8px 20px rgba(0,0,0,0.06); }
  .cover img { width: 100%; height: 100%; object-fit: cover; }
  .placeholder-title { font-family: 'Lora', serif; font-size: 14px; text-align: center; padding: 12px; color: var(--ink-muted); }
  .book-title { font-family: 'Lora', serif; font-size: 15px; font-weight: 600; line-height: 1.3; }
  .book-genre { font-size: 12px; color: var(--ink-muted); }

  /* Detalhes do Livro */
  .book-header { display: flex; gap: 24px; margin-bottom: 32px; }
  .book-header .cover { width: 140px; flex-shrink: 0; }
  .book-header .info { display: flex; flex-direction: column; gap: 8px; }
  .book-header h1 { font-family: 'Lora', serif; font-size: 28px; }
  .book-header .synopsis { font-size: 14px; color: var(--ink-muted); margin-top: 8px; }

  /* Lista de Capítulos */
  .chapter-list { display: flex; flex-direction: column; gap: 8px; }
  .chapter-row {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 12px 16px;
    background: var(--paper);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    transition: border-color 0.2s;
  }
  .chapter-row:hover { border-color: var(--ink-muted); }
  .chapter-title { font-size: 14px; font-weight: 500; }
  .chapter-actions { display: flex; gap: 6px; }

  /* Leitor */
  .reader { margin-top: 20px; }
  .reader h1 { font-family: 'Lora', serif; font-size: 28px; margin-bottom: 24px; text-align: center; }
  .reader .content {
    font-family: 'Lora', serif;
    font-size: 18px;
    line-height: 1.8;
    color: var(--ink);
    white-space: pre-wrap;
    max-width: 65ch;
    margin: 0 auto;
  }
  .reader-nav { display: flex; justify-content: space-between; margin-top: 48px; padding-top: 24px; border-top: 1px solid var(--border); }

  /* Modais */
  .modal-backdrop {
    position: fixed; inset: 0; background: rgba(0,0,0,0.4);
    display: flex; align-items: center; justify-content: center; padding: 20px; z-index: 100;
  }
  .modal {
    background: var(--paper);
    border-radius: var(--radius);
    max-width: 480px; width: 100%;
    padding: 24px;
    border: 1px solid var(--border);
  }
  .modal h2 { font-family: 'Lora', serif; font-size: 20px; margin-bottom: 16px; }
  .field { margin-bottom: 14px; }
  .field label { display: block; font-size: 12px; font-weight: 500; color: var(--ink-muted); margin-bottom: 4px; }
  .field input, .field select, .field textarea {
    width: 100%; font-size: 14px; padding: 8px 10px;
    border-radius: var(--radius); border: 1px solid var(--border);
    background: var(--bg); color: var(--ink); font-family: inherit;
  }
  .field textarea { resize: vertical; min-height: 80px; }
  .field textarea.big { min-height: 200px; font-family: 'Lora', serif; }
  .modal-actions { display: flex; justify-content: flex-end; gap: 8px; margin-top: 20px; }

  .empty { text-align: center; padding: 40px; color: var(--ink-muted); border: 1px dashed var(--border); border-radius: var(--radius); }

  /* Conteúdo público: não há controles de edição no cliente. */
  .public-notice {
    margin-top: 28px;
    padding: 12px 14px;
    border: 1px solid var(--border);
    border-radius: var(--radius);
    color: var(--ink-muted);
    font-size: 12px;
  }

</style>

</head>
<body>
<div id="root"></div>

<script id="initial-data" type="application/json">
{
  "site": {
    "authorName": "Rafick Santos",
    "tagline": "Biblioteca Pessoal & Obras Autorais",
    "bio": "Espaço dedicado às minhas publicações, histórias e escritos.",
    "contactEmail": "raficksantos493@gmail.com"
  },
  "books": [
    {
      "id": "bk1",
      "title": "Cadernos de Itapetinga",
      "genre": "Crônicas",
      "status": "em-andamento",
      "cover": "",
      "synopsis": "Uma coleção de crônicas curtas sobre o dia a dia, memórias e o interior da Bahia.",
      "chapters": [
        {
          "id": "ch1",
          "title": "Capítulo 1 — A fila do ônibus",
          "content": "Escreva aqui o texto do seu capítulo..."
        }
      ]
    }
  ]
}
</script>

<script>
(function () {
  "use strict";

  const initialEl = document.getElementById("initial-data");

  let state = { site: {}, books: [] };
  try {
    state = JSON.parse(initialEl.textContent);
  } catch (e) {
    console.error("Não foi possível carregar os dados públicos.");
  }

  function escapeHtml(value) {
    if (value == null) return "";
    return String(value)
      .replace(/&/g, "&amp;")
      .replace(/</g, "&lt;")
      .replace(/>/g, "&gt;")
      .replace(/"/g, "&quot;")
      .replace(/'/g, "&#039;");
  }

  function getBook(id) {
    return state.books.find(b => b.id === id);
  }

  function render() {
    const hash = window.location.hash.slice(1) || "/";
    const root = document.getElementById("root");

    const topBar = `
      <div class="top-bar">
        <a href="#/" style="font-weight: 600; font-size: 14px; letter-spacing: -0.5px;">
          ${escapeHtml(state.site.authorName)}
        </a>
      </div>
    `;

    if (hash === "/") {
      root.innerHTML = topBar + renderHome();
    } else if (hash.startsWith("/book/")) {
      root.innerHTML = topBar + renderBook(hash.split("/")[2]);
    } else if (hash.startsWith("/read/")) {
      const parts = hash.split("/");
      root.innerHTML = topBar + renderRead(parts[2], parts[3]);
    } else {
      root.innerHTML = topBar +
        `<div class="empty">Página não encontrada.<br><br><a href="#/" class="btn">Voltar</a></div>`;
    }
  }

  function renderHome() {
    let html = `
      <header class="hero">
        <h1>${escapeHtml(state.site.authorName)}</h1>
        <p class="tagline">${escapeHtml(state.site.tagline)}</p>
        <p class="bio">${escapeHtml(state.site.bio)}</p>
      </header>

      <section>
        <div class="section-head">
          <h2>Meus Livros</h2>
        </div>
    `;

    if (!Array.isArray(state.books) || state.books.length === 0) {
      html += `<div class="empty">Nenhum livro publicado ainda.</div>`;
    } else {
      html += `<div class="shelf">`;

      state.books.forEach(b => {
        const coverHtml = b.cover
          ? `<img src="${escapeHtml(b.cover)}" alt="Capa de ${escapeHtml(b.title)}" loading="lazy">`
          : `<div class="placeholder-title">${escapeHtml(b.title)}</div>`;

        html += `
          <a href="#/book/${encodeURIComponent(b.id)}" class="book-card">
            <div class="cover">${coverHtml}</div>
            <div>
              <div class="book-title">${escapeHtml(b.title)}</div>
              <div class="book-genre">${escapeHtml(b.genre)}</div>
            </div>
          </a>
        `;
      });

      html += `</div>`;
    }

    html += `</section>`;
    return html;
  }

  function renderBook(bookId) {
    const b = getBook(decodeURIComponent(bookId));

    if (!b) {
      return `<div class="empty">Livro não encontrado.<br><br><a href="#/" class="btn">Voltar</a></div>`;
    }

    const coverHtml = b.cover
      ? `<img src="${escapeHtml(b.cover)}" alt="Capa de ${escapeHtml(b.title)}">`
      : `<div class="placeholder-title">${escapeHtml(b.title)}</div>`;

    let html = `
      <div style="margin-bottom: 20px;">
        <a href="#/" style="font-size: 13px; color: var(--ink-muted);">← Voltar ao Início</a>
      </div>

      <div class="book-header">
        <div class="cover">${coverHtml}</div>
        <div class="info">
          <h1>${escapeHtml(b.title)}</h1>
          <div class="book-genre">
            ${escapeHtml(b.genre)} • Status: ${escapeHtml(b.status)}
          </div>
          <p class="synopsis">${escapeHtml(b.synopsis)}</p>
        </div>
      </div>

      <section>
        <div class="section-head">
          <h2>Índice</h2>
        </div>
    `;

    if (!Array.isArray(b.chapters) || b.chapters.length === 0) {
      html += `<div class="empty">Nenhum capítulo disponível.</div>`;
    } else {
      html += `<div class="chapter-list">`;

      b.chapters.forEach((ch, idx) => {
        html += `
          <div class="chapter-row">
            <a href="#/read/${encodeURIComponent(b.id)}/${encodeURIComponent(ch.id)}" class="chapter-title">
              ${idx + 1}. ${escapeHtml(ch.title)}
            </a>
          </div>
        `;
      });

      html += `</div>`;
    }

    html += `</section>`;
    return html;
  }

  function renderRead(bookId, chId) {
    const b = getBook(decodeURIComponent(bookId));

    if (!b) {
      return `<div class="empty">Livro não encontrado.</div>`;
    }

    const chapters = Array.isArray(b.chapters) ? b.chapters : [];
    const decodedChapterId = decodeURIComponent(chId);
    const idx = chapters.findIndex(c => c.id === decodedChapterId);

    if (idx === -1) {
      return `<div class="empty">Capítulo não encontrado.</div>`;
    }

    const ch = chapters[idx];
    const prev = chapters[idx - 1];
    const next = chapters[idx + 1];

    return `
      <div style="margin-bottom: 40px; text-align: center;">
        <a href="#/book/${encodeURIComponent(b.id)}" style="font-size: 13px; color: var(--ink-muted);">
          ← Índice de ${escapeHtml(b.title)}
        </a>
      </div>

      <article class="reader">
        <h1>${escapeHtml(ch.title)}</h1>
        <div class="content">${escapeHtml(ch.content)}</div>
      </article>

      <div class="reader-nav">
        <div>
          ${prev
            ? `<a href="#/read/${encodeURIComponent(b.id)}/${encodeURIComponent(prev.id)}" class="btn">← Capítulo Anterior</a>`
            : ""}
        </div>
        <div>
          ${next
            ? `<a href="#/read/${encodeURIComponent(b.id)}/${encodeURIComponent(next.id)}" class="btn">Próximo Capítulo →</a>`
            : ""}
        </div>
      </div>
    `;
  }

  window.addEventListener("hashchange", render);
  render();
})();
</script>
</body>
</html>
