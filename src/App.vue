<template>
  <div class="min-h-screen bg-slate-50 text-slate-800 md:flex md:flex-row">
    <aside
      class="w-full bg-slate-900 px-4 py-4 text-slate-100 shadow-md md:fixed md:inset-y-0 md:left-0 md:w-72 md:px-5 md:py-6"
    >
      <div class="flex items-center gap-3 rounded-2xl bg-slate-800/80 px-4 py-3">
        <div class="rounded-xl bg-cyan-400/20 p-2 text-cyan-300">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 24 24" fill="none" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.8" d="M12 3v18m9-9H3" />
          </svg>
        </div>
        <div>
          <p class="text-xs uppercase tracking-[0.2em] text-slate-400">Vice-Diretor IA</p>
          <p class="text-lg font-semibold tracking-tight">Atlas</p>
        </div>
      </div>

      <nav class="mt-6 grid grid-cols-2 gap-2 md:grid-cols-1">
        <button
          type="button"
          class="flex items-center gap-3 rounded-xl px-3 py-2.5 text-left text-sm transition"
          :class="tabClass('dashboard')"
          @click="currentTab = 'dashboard'"
        >
          <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" viewBox="0 0 24 24" fill="none" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.8" d="M3 13h8V3H3v10Zm10 8h8V11h-8v10ZM3 21h8v-6H3v6Zm10-10h8V3h-8v8Z" />
          </svg>
          Dashboard
        </button>

        <button
          type="button"
          class="flex items-center gap-3 rounded-xl px-3 py-2.5 text-left text-sm transition"
          :class="tabClass('alunos')"
          @click="currentTab = 'alunos'"
        >
          <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" viewBox="0 0 24 24" fill="none" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.8" d="M16 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2m20 0v-2a4 4 0 0 0-3-3.87M16 3.13a4 4 0 0 1 0 7.75M13 7a4 4 0 1 1-8 0 4 4 0 0 1 8 0Z" />
          </svg>
          Alunos
        </button>

        <button
          type="button"
          class="flex items-center gap-3 rounded-xl px-3 py-2.5 text-left text-sm transition"
          :class="tabClass('professores')"
          @click="currentTab = 'professores'"
        >
          <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" viewBox="0 0 24 24" fill="none" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.8" d="M20 21v-2a4 4 0 0 0-3-3.87M4 21v-2a4 4 0 0 1 3-3.87m9-4.13a4 4 0 1 0 0-8 4 4 0 0 0 0 8Zm-8 0a4 4 0 1 0 0-8 4 4 0 0 0 0 8Z" />
          </svg>
          Professores
        </button>

        <button
          type="button"
          class="flex items-center gap-3 rounded-xl px-3 py-2.5 text-left text-sm transition"
          :class="tabClass('financeiro')"
          @click="currentTab = 'financeiro'"
        >
          <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" viewBox="0 0 24 24" fill="none" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.8" d="M2 10h20M6 14h.01M10 14h2m8-9H4a2 2 0 0 0-2 2v10a2 2 0 0 0 2 2h16a2 2 0 0 0 2-2V7a2 2 0 0 0-2-2Z" />
          </svg>
          Financeiro
        </button>

        <button
          type="button"
          class="col-span-2 flex items-center gap-3 rounded-xl px-3 py-2.5 text-left text-sm transition md:col-span-1"
          :class="tabClass('configuracoes')"
          @click="currentTab = 'configuracoes'"
        >
          <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" viewBox="0 0 24 24" fill="none" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.8" d="M12 15.5A3.5 3.5 0 1 0 12 8.5a3.5 3.5 0 0 0 0 7Zm7.94-2.5a1.5 1.5 0 0 0 .3 1.64l.05.05a2 2 0 1 1-2.83 2.83l-.05-.05a1.5 1.5 0 0 0-1.64-.3 1.5 1.5 0 0 0-.93 1.37V19a2 2 0 1 1-4 0v-.08a1.5 1.5 0 0 0-.93-1.37 1.5 1.5 0 0 0-1.64.3l-.05.05a2 2 0 1 1-2.83-2.83l.05-.05a1.5 1.5 0 0 0 .3-1.64 1.5 1.5 0 0 0-1.37-.93H5a2 2 0 1 1 0-4h.08a1.5 1.5 0 0 0 1.37-.93 1.5 1.5 0 0 0-.3-1.64l-.05-.05a2 2 0 1 1 2.83-2.83l.05.05a1.5 1.5 0 0 0 1.64.3h.01a1.5 1.5 0 0 0 .92-1.38V5a2 2 0 1 1 4 0v.08a1.5 1.5 0 0 0 .93 1.37 1.5 1.5 0 0 0 1.64-.3l.05-.05a2 2 0 1 1 2.83 2.83l-.05.05a1.5 1.5 0 0 0-.3 1.64v.01a1.5 1.5 0 0 0 1.38.92H19a2 2 0 1 1 0 4h-.08a1.5 1.5 0 0 0-1.37.93Z" />
          </svg>
          Configurações
        </button>
      </nav>
    </aside>

    <main class="flex w-full flex-col gap-6 px-4 py-4 sm:px-6 md:ml-72 md:px-8 md:py-6">
      <header class="rounded-2xl bg-white p-3 shadow-[0_2px_10px_-3px_rgba(6,81,237,0.1)]">
        <div class="flex flex-col gap-3 md:flex-row md:items-center md:justify-between">
          <div class="flex items-center gap-2 rounded-xl border border-slate-200 bg-slate-50 px-3 py-2">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4 text-slate-500" viewBox="0 0 24 24" fill="none" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.8" d="m21 21-4.34-4.34M11 18a7 7 0 1 1 0-14 7 7 0 0 1 0 14Z" />
            </svg>
            <input
              type="text"
              placeholder="Buscar aluno, turma, alerta ou indicador..."
              class="w-full bg-transparent text-sm text-slate-700 placeholder:text-slate-400 focus:outline-none md:w-96"
            />
          </div>

          <div class="flex items-center gap-3 self-end md:self-auto">
            <button type="button" class="rounded-xl border border-slate-200 bg-white p-2.5 text-slate-500 hover:bg-slate-100">
              <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 24 24" fill="none" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.8" d="M15 17h5l-1.4-1.4A2 2 0 0 1 18 14.2V11a6 6 0 1 0-12 0v3.2a2 2 0 0 1-.6 1.4L4 17h5m2 0v1a2 2 0 1 0 4 0v-1m-4 0h4" />
              </svg>
            </button>
            <div class="flex items-center gap-2 rounded-xl border border-slate-200 bg-white px-2 py-1.5">
              <img
                src="https://ui-avatars.com/api/?name=Diretor+Carlos&background=0D8ABC&color=fff"
                alt="Diretor Carlos"
                class="h-8 w-8 rounded-lg object-cover"
              />
              <p class="text-sm font-medium text-slate-700">Diretor Carlos</p>
            </div>
          </div>
        </div>
      </header>

      <section class="flex flex-col gap-2 rounded-2xl bg-white p-5 shadow-sm">
        <p class="text-sm font-medium text-slate-500">{{ formattedDate }}</p>
        <h1 class="text-2xl font-semibold tracking-tight text-slate-900 sm:text-3xl">
          {{ pageHeader.title }}
        </h1>
        <p class="text-sm text-slate-600">{{ pageHeader.subtitle }}</p>
      </section>

      <section v-if="currentTab === 'dashboard'" class="flex flex-col gap-6">
        <section class="grid grid-cols-1 gap-4 sm:grid-cols-2 xl:grid-cols-4">
          <article
            v-for="kpi in kpiCards"
            :key="kpi.id"
            class="rounded-2xl bg-white p-5 shadow-[0_2px_10px_-3px_rgba(6,81,237,0.1)]"
          >
            <div class="mb-3 flex items-center justify-between">
              <p class="text-sm font-medium text-slate-500">{{ kpi.label }}</p>
              <span class="rounded-lg bg-slate-100 p-2 text-slate-500">
                <svg
                  v-if="kpi.id === 'frequency'"
                  xmlns="http://www.w3.org/2000/svg"
                  class="h-4 w-4"
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                >
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.8" d="M3 12h18M12 3v18" />
                </svg>
                <svg
                  v-else-if="kpi.id === 'average'"
                  xmlns="http://www.w3.org/2000/svg"
                  class="h-4 w-4"
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                >
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.8" d="M4 18h16M7 14l3-3 3 2 4-5" />
                </svg>
                <svg
                  v-else-if="kpi.id === 'overdue'"
                  xmlns="http://www.w3.org/2000/svg"
                  class="h-4 w-4"
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                >
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.8" d="M2 10h20M6 14h.01M10 14h2m8-9H4a2 2 0 0 0-2 2v10a2 2 0 0 0 2 2h16a2 2 0 0 0 2-2V7a2 2 0 0 0-2-2Z" />
                </svg>
                <svg
                  v-else
                  xmlns="http://www.w3.org/2000/svg"
                  class="h-4 w-4"
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                >
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.8" d="M16 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2m20 0v-2a4 4 0 0 0-3-3.87M16 3.13a4 4 0 0 1 0 7.75M13 7a4 4 0 1 1-8 0 4 4 0 0 1 8 0Z" />
                </svg>
              </span>
            </div>
            <p class="text-3xl font-semibold tracking-tight text-slate-900">{{ kpi.value }}</p>
            <p class="mt-1 text-xs text-slate-500">Atualização contínua por IA</p>
          </article>
        </section>

        <section class="grid grid-cols-1 gap-6 xl:grid-cols-3">
          <article class="rounded-2xl bg-white p-5 shadow-[0_2px_10px_-3px_rgba(239,68,68,0.2)] xl:col-span-2">
            <div class="flex flex-col gap-2 pb-4 sm:flex-row sm:items-center sm:justify-between">
              <h2 class="text-xl font-semibold text-slate-900">Alertas Críticos</h2>
              <span class="inline-flex w-fit rounded-full bg-red-100 px-3 py-1 text-xs font-semibold text-red-700">Acompanhamento em tempo real</span>
            </div>

            <div v-if="isAILoading" class="grid grid-cols-1 gap-4 lg:grid-cols-2">
              <div
                v-for="idx in 3"
                :key="`critical-skeleton-${idx}`"
                class="flex flex-col gap-3 rounded-2xl bg-slate-100/80 p-4"
              >
                <div class="h-5 w-1/2 animate-pulse rounded bg-slate-200"></div>
                <div class="h-4 w-1/3 animate-pulse rounded bg-slate-200"></div>
                <div class="h-3 w-full animate-pulse rounded bg-slate-200"></div>
                <div class="h-3 w-11/12 animate-pulse rounded bg-slate-200"></div>
                <div class="h-10 w-full animate-pulse rounded-xl bg-slate-200"></div>
              </div>
              <p class="lg:col-span-2 text-sm text-slate-500">Atlas processando dados da escola...</p>
            </div>

            <div v-else class="grid grid-cols-1 gap-4 lg:grid-cols-2">
              <article
                v-for="alert in atlasData.ai_critical_alerts"
                :key="alert.id"
                class="flex h-full flex-col gap-3 rounded-2xl bg-slate-50 p-4"
              >
                <div class="flex flex-wrap gap-2">
                  <span class="rounded-full px-2.5 py-1 text-xs font-semibold" :class="categoryBadgeClass(alert.category)">
                    {{ alert.category }}
                  </span>
                  <span
                    class="rounded-full px-2.5 py-1 text-xs font-semibold"
                    :class="alert.severity === 'high' ? 'bg-red-100 text-red-700' : 'bg-amber-100 text-amber-700'"
                  >
                    Prioridade {{ alert.severity === 'high' ? 'Alta' : 'Média' }}
                  </span>
                </div>
                <div>
                  <h3 class="text-base font-semibold text-slate-900">{{ alert.student }}</h3>
                  <p class="text-sm text-slate-600">{{ alert.grade }}</p>
                </div>
                <ul class="list-disc space-y-1 pl-5 text-sm text-slate-700">
                  <li v-for="trigger in alert.ai_triggers" :key="trigger">{{ trigger }}</li>
                </ul>
                <button type="button" class="alert-action-btn mt-auto w-full">
                  {{ alert.suggested_action }}
                </button>
              </article>
            </div>
          </article>

          <div class="flex flex-col gap-6">
            <article class="rounded-2xl bg-white p-5 shadow-[0_2px_10px_-3px_rgba(6,81,237,0.1)]">
              <div class="mb-4 flex items-center justify-between">
                <h2 class="text-lg font-semibold text-slate-900">Insight Pedagógico</h2>
                <span class="rounded-full bg-cyan-100 px-2.5 py-1 text-xs font-semibold text-cyan-700">IA</span>
              </div>

              <div v-if="isAILoading" class="flex flex-col gap-3">
                <div class="h-4 w-2/3 animate-pulse rounded bg-slate-200"></div>
                <div class="h-3 w-full animate-pulse rounded bg-slate-200"></div>
                <div class="h-3 w-full animate-pulse rounded bg-slate-200"></div>
                <div class="h-16 w-full animate-pulse rounded-xl bg-slate-200"></div>
              </div>

              <div v-else class="flex flex-col gap-4">
                <p class="text-sm font-medium text-slate-500">{{ atlasData.academic_insights.target }} · {{ atlasData.academic_insights.subject }}</p>
                <div class="flex h-20 items-end gap-2 rounded-xl bg-slate-100 px-3 pb-3 pt-2">
                  <div class="w-full rounded-md bg-cyan-200" style="height: 28%"></div>
                  <div class="w-full rounded-md bg-cyan-300" style="height: 42%"></div>
                  <div class="w-full rounded-md bg-cyan-400" style="height: 63%"></div>
                  <div class="w-full rounded-md bg-cyan-500" style="height: 79%"></div>
                  <div class="w-full rounded-md bg-cyan-300" style="height: 51%"></div>
                  <div class="w-full rounded-md bg-cyan-400" style="height: 68%"></div>
                </div>
                <p class="text-sm leading-relaxed text-slate-700">{{ atlasData.academic_insights.ai_analysis }}</p>
                <div class="rounded-xl bg-cyan-50 p-3 text-sm text-cyan-900">
                  <strong>Ação sugerida:</strong> {{ atlasData.academic_insights.suggested_action }}
                </div>
              </div>
            </article>

            <section class="rounded-2xl bg-gradient-to-r from-cyan-50 to-sky-100 p-4 shadow-md sm:p-5">
              <label for="atlas-chat" class="mb-3 block text-lg font-semibold text-slate-900">Pergunte aos dados da escola</label>
              <div class="flex flex-col gap-3">
                <input
                  id="atlas-chat"
                  type="text"
                  class="w-full rounded-xl border border-sky-100 bg-white px-4 py-3 text-sm text-slate-700 placeholder:text-slate-400 focus:border-cyan-500 focus:outline-none focus:ring-2 focus:ring-cyan-200"
                  placeholder="Ex: Como está a inadimplência comparada ao mês passado?"
                />
                <button
                  type="button"
                  class="h-10 w-full rounded-xl bg-slate-900 px-4 text-sm font-semibold text-white transition hover:bg-slate-700 focus:outline-none focus:ring-2 focus:ring-slate-900 focus:ring-offset-2"
                >
                  Enviar pergunta
                </button>
              </div>
            </section>
          </div>
        </section>
      </section>

      <section v-else-if="currentTab === 'alunos'" class="flex flex-col gap-6">
        <section class="grid grid-cols-1 gap-4 md:grid-cols-3">
          <article class="rounded-2xl bg-white p-5 shadow-sm">
            <p class="text-sm font-medium text-slate-500">Risco de Evasão Crítico</p>
            <p class="mt-1 text-3xl font-semibold tracking-tight text-slate-900">14 alunos</p>
            <p class="mt-2 text-xs font-medium text-rose-600">Impacto projetado: -R$ 21.000/mês</p>
          </article>

          <article class="rounded-2xl bg-white p-5 shadow-sm">
            <p class="text-sm font-medium text-slate-500">Anomalias de Desempenho</p>
            <p class="mt-1 text-3xl font-semibold tracking-tight text-slate-900">28 alertas</p>
            <p class="mt-2 text-xs font-medium text-slate-500">Maior concentração no 1º Ano Médio</p>
          </article>

          <article class="rounded-2xl bg-white p-5 shadow-sm">
            <p class="text-sm font-medium text-slate-500">Resgates Bem-sucedidos</p>
            <p class="mt-1 text-3xl font-semibold tracking-tight text-slate-900">5 alunos</p>
            <p class="mt-2 text-xs font-medium text-emerald-600">Retornaram ao status Estável nesta semana</p>
          </article>
        </section>

        <section class="rounded-2xl bg-white p-4 shadow-sm">
          <div class="flex flex-wrap gap-2">
            <button
              type="button"
              class="h-10 rounded-full px-4 text-sm font-semibold transition"
              :class="filterPillClass('Todos')"
              @click="currentFilter = 'Todos'"
            >
              Todos os alunos
            </button>
            <button
              type="button"
              class="h-10 rounded-full px-4 text-sm font-semibold transition"
              :class="filterPillClass('Risco Crítico')"
              @click="currentFilter = 'Risco Crítico'"
            >
              🔴 Apenas Risco Crítico
            </button>
            <button
              type="button"
              class="h-10 rounded-full px-4 text-sm font-semibold transition"
              :class="filterPillClass('Queda em Exatas')"
              @click="currentFilter = 'Queda em Exatas'"
            >
              📉 Queda em Exatas
            </button>
            <button
              type="button"
              class="h-10 rounded-full px-4 text-sm font-semibold transition"
              :class="filterPillClass('Alerta Financeiro')"
              @click="currentFilter = 'Alerta Financeiro'"
            >
              💰 Alerta Financeiro
            </button>
          </div>
        </section>

        <article class="rounded-2xl bg-white p-5 shadow-[0_2px_10px_-3px_rgba(6,81,237,0.1)]">
          <div class="flex flex-col gap-1 pb-4">
            <h2 class="text-xl font-semibold text-slate-900">Alunos com Monitoramento Preditivo</h2>
            <p class="text-sm text-slate-600">Clique em um aluno para abrir o painel detalhado de cruzamento de dados.</p>
          </div>

          <div class="overflow-hidden rounded-2xl border border-slate-200">
            <table class="w-full border-collapse">
              <thead class="bg-slate-100 text-left text-xs uppercase tracking-wide text-slate-500">
                <tr>
                  <th class="px-4 py-3 font-semibold">Aluno</th>
                  <th class="px-4 py-3 font-semibold">Turma</th>
                  <th class="px-4 py-3 font-semibold">Status</th>
                  <th class="px-4 py-3 font-semibold">Risk Score</th>
                </tr>
              </thead>
              <tbody class="divide-y divide-slate-200 bg-white text-sm">
                <tr
                  v-for="student in filteredStudents"
                  :key="student.id"
                  class="cursor-pointer transition hover:bg-slate-50"
                  @click="selectedStudent = student"
                >
                  <td class="px-4 py-3 font-medium text-slate-900">{{ student.name }}</td>
                  <td class="px-4 py-3 text-slate-600">{{ student.grade }}</td>
                  <td class="px-4 py-3 text-slate-600">{{ student.status }}</td>
                  <td class="px-4 py-3">
                    <span class="rounded-full px-2.5 py-1 text-xs font-semibold" :class="riskBadgeClass(student.riskScore)">
                      {{ student.riskScore }}
                    </span>
                  </td>
                </tr>
              </tbody>
            </table>
          </div>
        </article>
      </section>

      <section v-else-if="currentTab === 'professores'" class="grid grid-cols-1 gap-4 xl:grid-cols-2">
        <article
          v-for="teacher in teachersData"
          :key="teacher.id"
          class="rounded-2xl bg-white p-5 shadow-sm"
        >
          <div class="flex items-start justify-between gap-3">
            <div class="flex items-center gap-3">
              <img
                :src="`https://ui-avatars.com/api/?name=${encodeURIComponent(teacher.name)}&background=0D8ABC&color=fff`"
                :alt="teacher.name"
                class="h-12 w-12 rounded-xl object-cover"
              />
              <div>
                <p class="font-semibold text-slate-900">{{ teacher.name }}</p>
                <p class="text-sm text-slate-600">{{ teacher.discipline }}</p>
              </div>
            </div>
            <span
              class="rounded-full px-2.5 py-1 text-xs font-semibold"
              :class="teacher.burnoutRisk === 'alto' ? 'bg-rose-100 text-rose-700' : 'bg-emerald-100 text-emerald-700'"
            >
              Risco {{ teacher.burnoutRisk === 'alto' ? 'Alto' : 'Baixo' }}
            </span>
          </div>

          <div class="mt-4 flex flex-col gap-2">
            <div class="flex items-center justify-between text-xs font-medium text-slate-500">
              <span>Burnout Risk</span>
              <span>{{ teacher.burnoutScore }}%</span>
            </div>
            <div class="h-2 w-full rounded-full bg-slate-100">
              <div
                class="h-2 rounded-full transition-all"
                :class="teacher.burnoutRisk === 'alto' ? 'bg-rose-500' : 'bg-emerald-500'"
                :style="{ width: `${teacher.burnoutScore}%` }"
              ></div>
            </div>
          </div>

          <p class="mt-3 text-sm text-slate-600">{{ teacher.metrics }}</p>
          <div class="mt-4 rounded-xl bg-indigo-50 p-3 text-sm text-indigo-900">
            <strong>Insight IA:</strong> {{ teacher.ai_insight }}
          </div>
        </article>
      </section>

      <section v-else-if="currentTab === 'financeiro'" class="flex flex-col gap-6">
        <article class="rounded-2xl bg-white p-5 shadow-sm">
          <div class="flex flex-col gap-4 lg:flex-row lg:items-center lg:justify-between">
            <div class="flex flex-col gap-1">
              <h2 class="text-xl font-semibold text-slate-900">Previsão de Receita do Mês</h2>
              <p class="text-sm text-slate-600">
                A IA ajusta a projeção considerando inadimplência crônica, anomalias de atraso e recuperação provável.
              </p>
            </div>
            <span class="rounded-full bg-cyan-100 px-3 py-1 text-xs font-semibold text-cyan-700">Ajuste Preditivo</span>
          </div>

          <div class="mt-4 grid grid-cols-1 gap-4 md:grid-cols-2">
            <div class="rounded-xl bg-slate-100 p-4">
              <p class="text-xs uppercase tracking-wide text-slate-500">Receita Esperada (ERP)</p>
              <p class="mt-1 text-2xl font-semibold text-slate-900">R$ 520.000</p>
              <p class="mt-1 text-xs text-slate-500">Composição: 85% Mensalidades regulares | 15% Taxas extras</p>
            </div>
            <div class="rounded-xl bg-cyan-50 p-4">
              <p class="text-xs uppercase tracking-wide text-cyan-700">Receita Realista (Ajuste IA)</p>
              <p class="mt-1 text-2xl font-semibold text-cyan-900">R$ 435.000</p>
            </div>
          </div>

          <p class="mt-3 text-sm text-slate-600">
            Insight IA: a previsão foi ajustada em <strong class="text-slate-900">R$ 85 mil</strong> com base no padrão de
            inadimplência recorrente e probabilidade de recuperação parcial neste ciclo.
          </p>

          <div class="mt-4 grid grid-cols-1 gap-3 md:grid-cols-2">
            <div class="rounded-xl border border-rose-100 bg-rose-50 p-4">
              <p class="text-sm font-semibold text-slate-900">Detalhamento da Retenção da IA (-R$ 85.000)</p>
              <ul class="mt-2 space-y-1 text-xs text-slate-600">
                <li class="flex items-center justify-between gap-2">
                  <span>Inadimplência crônica projetada</span>
                  <span class="font-semibold text-rose-600">-R$ 50.000</span>
                </li>
                <li class="flex items-center justify-between gap-2">
                  <span>Risco alto de evasão no mês</span>
                  <span class="font-semibold text-rose-600">-R$ 35.000</span>
                </li>
              </ul>
            </div>
            <div class="rounded-xl border border-cyan-100 bg-cyan-50 p-4">
              <p class="text-sm font-semibold text-slate-900">Ações Recomendadas para Recuperação</p>
              <div class="mt-2 flex flex-col gap-2">
                <button
                  type="button"
                  class="h-9 rounded-lg bg-cyan-600 px-3 text-left text-xs font-semibold text-white transition hover:bg-cyan-700"
                >
                  ✨ Lançar campanha de desconto pontualidade
                </button>
                <button
                  type="button"
                  class="h-9 rounded-lg bg-slate-800 px-3 text-left text-xs font-semibold text-white transition hover:bg-slate-700"
                >
                  ✨ Gerar propostas de parcelamento em lote
                </button>
              </div>
            </div>
          </div>
        </article>

        <article class="rounded-2xl bg-white p-5 shadow-md">
          <div class="flex flex-col gap-1 pb-4">
            <h2 class="text-xl font-semibold text-slate-900">Cobrança Inteligente</h2>
            <p class="text-sm text-slate-600">Priorização preditiva de contato com base no histórico e anomalias de atraso.</p>
          </div>

          <div class="overflow-hidden rounded-2xl border border-slate-200">
            <table class="w-full border-collapse">
              <thead class="bg-slate-100 text-left text-xs uppercase tracking-wide text-slate-500">
                <tr>
                  <th class="px-4 py-3 font-semibold">Família</th>
                  <th class="px-4 py-3 font-semibold">Valor</th>
                  <th class="px-4 py-3 font-semibold">Perfil de Pagamento</th>
                  <th class="px-4 py-3 font-semibold">Ação Sugerida</th>
                </tr>
              </thead>
              <tbody class="divide-y divide-slate-200 bg-white text-sm">
                <tr v-for="entry in financeData" :key="entry.id" class="hover:bg-slate-50">
                  <td class="px-4 py-3">
                    <p class="font-medium text-slate-900">{{ entry.nome_responsavel }}</p>
                    <p class="text-xs text-slate-500">Aluno: {{ entry.aluno }}</p>
                  </td>
                  <td class="px-4 py-3 font-semibold text-slate-900">{{ entry.debt }}</td>
                  <td class="px-4 py-3">
                    <p class="text-slate-700">{{ entry.status }}</p>
                    <p class="mt-1 text-xs text-slate-500">{{ entry.ai_recommendation }}</p>
                  </td>
                  <td class="px-4 py-3">
                    <button
                      type="button"
                      class="h-10 w-40 rounded-xl px-4 text-sm font-semibold text-white shadow-sm transition"
                      :class="entry.status === 'Atraso Anômalo' ? 'bg-indigo-600 hover:bg-indigo-700' : 'bg-slate-800 hover:bg-slate-700'"
                    >
                      {{ entry.status === 'Atraso Anômalo' ? 'Gerar Acordo' : 'Notificar' }}
                    </button>
                  </td>
                </tr>
              </tbody>
            </table>
          </div>
        </article>
      </section>

      <section v-else-if="currentTab === 'configuracoes'" class="flex flex-col gap-6">
        <article class="rounded-2xl bg-white p-5 shadow-sm">
          <div class="pb-4">
            <h2 class="text-xl font-semibold text-slate-900">Configurações do Vice-Diretor Digital</h2>
            <p class="text-sm text-slate-600">Ajuste como a IA deve interagir com rotinas críticas da escola.</p>
          </div>

          <div class="grid grid-cols-1 gap-4">
            <label class="flex items-center justify-between gap-4 rounded-xl border border-slate-200 p-4">
              <div>
                <p class="font-medium text-slate-900">Disparo Automático de WhatsApp para Evasão</p>
                <p class="text-sm text-slate-500">Envia mensagens preventivas para famílias em risco alto.</p>
              </div>
              <span class="relative inline-flex h-6 w-11 items-center">
                <input v-model="settings.autoWhatsapp" type="checkbox" class="peer sr-only" />
                <span class="h-6 w-11 rounded-full bg-slate-300 transition peer-checked:bg-cyan-500"></span>
                <span class="absolute left-1 h-4 w-4 rounded-full bg-white transition peer-checked:translate-x-5"></span>
              </span>
            </label>

            <label class="flex items-center justify-between gap-4 rounded-xl border border-slate-200 p-4">
              <div>
                <p class="font-medium text-slate-900">Ajuste de Sensibilidade do Risco</p>
                <p class="text-sm text-slate-500">Ativa alertas antecipados para pequenas variações de comportamento.</p>
              </div>
              <span class="relative inline-flex h-6 w-11 items-center">
                <input v-model="settings.riskSensitivity" type="checkbox" class="peer sr-only" />
                <span class="h-6 w-11 rounded-full bg-slate-300 transition peer-checked:bg-cyan-500"></span>
                <span class="absolute left-1 h-4 w-4 rounded-full bg-white transition peer-checked:translate-x-5"></span>
              </span>
            </label>

            <label class="flex items-center justify-between gap-4 rounded-xl border border-slate-200 p-4">
              <div>
                <p class="font-medium text-slate-900">Sincronização ERP Legado</p>
                <p class="text-sm text-slate-500">Sincroniza dados financeiros e acadêmicos com sistemas externos.</p>
              </div>
              <span class="relative inline-flex h-6 w-11 items-center">
                <input v-model="settings.erpSync" type="checkbox" class="peer sr-only" />
                <span class="h-6 w-11 rounded-full bg-slate-300 transition peer-checked:bg-cyan-500"></span>
                <span class="absolute left-1 h-4 w-4 rounded-full bg-white transition peer-checked:translate-x-5"></span>
              </span>
            </label>
          </div>
        </article>
      </section>
    </main>

    <transition
      enter-active-class="transition duration-300 ease-out"
      enter-from-class="opacity-0"
      enter-to-class="opacity-100"
      leave-active-class="transition duration-200 ease-in"
      leave-from-class="opacity-100"
      leave-to-class="opacity-0"
    >
      <div v-if="selectedStudent" class="fixed inset-0 z-40 bg-slate-900/35" @click="selectedStudent = null"></div>
    </transition>

    <transition
      enter-active-class="transition duration-300 ease-out"
      enter-from-class="translate-x-full"
      enter-to-class="translate-x-0"
      leave-active-class="transition duration-200 ease-in"
      leave-from-class="translate-x-0"
      leave-to-class="translate-x-full"
    >
      <aside
        v-if="selectedStudent"
        class="fixed inset-y-0 right-0 z-50 flex w-full max-w-md flex-col gap-5 overflow-y-auto bg-white p-5 pb-8 shadow-2xl"
      >
        <div class="flex items-start justify-between">
          <div class="flex items-center gap-3">
            <img
              :src="`https://ui-avatars.com/api/?name=${encodeURIComponent(selectedStudent.name)}&background=0D8ABC&color=fff`"
              :alt="selectedStudent.name"
              class="h-14 w-14 rounded-xl object-cover"
            />
            <div>
              <p class="text-base font-semibold text-slate-900">{{ selectedStudent.name }}</p>
              <p class="text-sm text-slate-600">{{ selectedStudent.grade }}</p>
            </div>
          </div>
          <button
            type="button"
            class="rounded-lg bg-slate-100 px-2.5 py-1.5 text-sm font-medium text-slate-600 hover:bg-slate-200"
            @click="selectedStudent = null"
          >
            Fechar
          </button>
        </div>

        <div class="grid grid-cols-1 gap-3 sm:grid-cols-3">
          <div class="rounded-xl bg-slate-50 p-3">
            <p class="text-xs uppercase tracking-wide text-slate-500">Frequência</p>
            <p class="mt-1 text-lg font-semibold text-slate-900">{{ selectedStudent.kpis.attendance }}</p>
          </div>
          <div class="rounded-xl bg-slate-50 p-3">
            <p class="text-xs uppercase tracking-wide text-slate-500">Média</p>
            <p class="mt-1 text-lg font-semibold text-slate-900">{{ selectedStudent.kpis.average }}</p>
          </div>
          <div class="rounded-xl bg-slate-50 p-3">
            <p class="text-xs uppercase tracking-wide text-slate-500">Financeiro</p>
            <p class="mt-1 text-lg font-semibold text-slate-900">{{ selectedStudent.kpis.financial }}</p>
          </div>
        </div>

        <div class="rounded-2xl border border-cyan-200 bg-cyan-50 p-4">
          <p class="text-xs uppercase tracking-wide text-cyan-700">Insight da IA</p>
          <p class="mt-2 text-sm leading-relaxed text-cyan-900">{{ selectedStudent.ai_analysis }}</p>
        </div>

        <div class="rounded-2xl bg-slate-900 p-4 text-white">
          <p class="text-xs uppercase tracking-wide text-slate-300">Risk Score</p>
          <div class="mt-1 flex items-end justify-between gap-3">
            <p class="text-3xl font-semibold transition-all duration-300">{{ displayedRiskScore }}</p>
            <span class="rounded-full px-2.5 py-1 text-xs font-semibold" :class="riskStatusTagClass">
              {{ displayedRiskStatus }}
            </span>
          </div>
          <p class="mt-2 text-xs font-medium text-cyan-300">{{ riskPanelTitle }}</p>
          <div class="mt-3 overflow-hidden rounded-xl bg-slate-800/80 p-3">
            <div v-for="item in riskBreakdownItems" :key="item.label" class="mb-2 last:mb-0">
              <div class="mb-1 flex items-center justify-between text-xs text-slate-200">
                <span>{{ item.label }}</span>
                <span>{{ item.value }}%</span>
              </div>
              <div class="h-2 rounded-full bg-slate-700">
                <div class="h-2 rounded-full bg-cyan-400 transition-all duration-300" :style="{ width: `${item.value}%` }"></div>
              </div>
            </div>
          </div>
        </div>

        <div class="rounded-2xl border border-slate-200 bg-white p-4 shadow-sm">
          <p class="text-sm font-semibold text-slate-900">{{ isStableSelected ? 'Ações de Engajamento' : 'Simulador de Ação (E se?)' }}</p>
          <p class="mt-1 text-xs text-slate-500">Selecione uma ação para visualizar o impacto estimado no risco.</p>
          <div class="mt-3 flex flex-wrap gap-2">
            <button
              v-for="option in simulationOptions"
              :key="option.value"
              type="button"
              class="h-10 rounded-xl px-4 text-sm font-semibold transition"
              :class="
                selectedSimulation === option.value
                  ? 'bg-cyan-600 text-white shadow-sm'
                  : 'bg-slate-100 text-slate-700 hover:bg-slate-200'
              "
              @click="selectedSimulation = option.value"
            >
              {{ option.label }}
            </button>
          </div>
        </div>

        <div class="rounded-2xl border border-cyan-200 bg-cyan-50 p-4">
          <button
            type="button"
            class="h-10 w-full rounded-xl bg-cyan-600 px-4 text-sm font-semibold text-white shadow-sm transition hover:bg-cyan-700"
            @click="showAICopilot = !showAICopilot"
          >
            {{ isStableSelected ? '✨ Gerar Mensagem de Reconhecimento' : '✨ Gerar Mensagem de Acolhimento' }}
          </button>

          <transition
            enter-active-class="transition-all duration-300 ease-out"
            enter-from-class="opacity-0 max-h-0"
            enter-to-class="opacity-100 max-h-80"
            leave-active-class="transition-all duration-200 ease-in"
            leave-from-class="opacity-100 max-h-80"
            leave-to-class="opacity-0 max-h-0"
          >
            <div v-if="showAICopilot" class="mt-3 overflow-hidden rounded-xl border border-cyan-200 bg-white p-3">
              <p class="text-xs uppercase tracking-wide text-cyan-700">Rascunho Gerado por IA</p>
              <p class="mt-2 text-sm leading-relaxed text-slate-700">{{ generatedCareMessage }}</p>
              <div class="mt-3 flex flex-wrap gap-2">
                <button
                  type="button"
                  class="h-10 rounded-xl bg-slate-900 px-4 text-sm font-semibold text-white transition hover:bg-slate-700"
                  @click="copyCareMessage"
                >
                  {{ copiedMessage ? 'Copiado!' : 'Copiar' }}
                </button>
                <button
                  type="button"
                  class="h-10 rounded-xl bg-emerald-600 px-4 text-sm font-semibold text-white transition hover:bg-emerald-700"
                >
                  Enviar via WhatsApp
                </button>
              </div>
            </div>
          </transition>
        </div>
      </aside>
    </transition>
  </div>
</template>

<script setup>
import { computed, reactive, ref, onMounted, watch } from 'vue'

const currentTab = ref('dashboard')
const selectedStudent = ref(null)
const currentFilter = ref('Todos')
const showAICopilot = ref(false)
const copiedMessage = ref(false)
const selectedSimulation = ref('none')

const atlasData = reactive({
  school_info: { name: 'Colégio Atlas', manager_name: 'Carlos', current_date: '2026-03-17' },
  kpis: { general_frequency: 92.5, academic_average: 7.8, overdue_bills: 12, total_active_students: 845 },
  ai_critical_alerts: [
    {
      id: 'risk_001',
      category: 'Evasão',
      type: 'evasion_risk',
      severity: 'high',
      student: 'Mariana Souza',
      grade: '9º Ano B',
      ai_triggers: [
        '3 faltas consecutivas não justificadas',
        'Mensalidade com 15 dias de atraso',
        'Queda de 30% no engajamento em sala'
      ],
      suggested_action: 'Contatar Família'
    },
    {
      id: 'risk_002',
      category: 'Desempenho',
      type: 'evasion_risk',
      severity: 'medium',
      student: 'Lucas Almeida',
      grade: '1º Ano Médio',
      ai_triggers: [
        'Queda brusca de notas em Exatas',
        'Acessos ao portal do aluno zerados nesta semana'
      ],
      suggested_action: 'Agendar Mentoria'
    },
    {
      id: 'risk_003',
      category: 'RH / Docente',
      type: 'staff_risk',
      severity: 'medium',
      student: 'Profª Fernanda Lima',
      grade: 'Ciências da Natureza',
      ai_triggers: [
        'Tempo médio de lançamento de notas subiu de 2 para 7 dias',
        'Assumiu 3 turmas extras de substituição neste mês'
      ],
      suggested_action: 'Rever Alocação'
    }
  ],
  academic_insights: {
    target: '9º Ano B',
    subject: 'Matemática',
    ai_analysis:
      'Identificado padrão de dificuldade coletiva em Geometria Espacial nas últimas duas semanas.',
    suggested_action: 'Disponibilizar trilha de reforço gamificada no portal e notificar professor.'
  }
})

const studentsData = reactive([
  {
    id: 1,
    name: 'Mariana Souza',
    grade: '9º Ano B',
    riskScore: 85,
    status: 'Risco Crítico',
    kpis: { attendance: '78%', average: '5.2', financial: '15 dias atraso' },
    ai_analysis:
      'O modelo preditivo aponta 85% de chance de evasão. A aluna acumula 3 faltas recentes, queda brusca em exatas e a família atrasou a primeira mensalidade no ano.'
  },
  {
    id: 2,
    name: 'Lucas Almeida',
    grade: '1º Ano Médio',
    riskScore: 60,
    status: 'Atenção',
    kpis: { attendance: '90%', average: '6.0', financial: 'Em dia' },
    ai_analysis:
      'Risco acadêmico detectado. Acessos ao portal caíram a zero. Sugestão de mentoria.'
  },
  {
    id: 3,
    name: 'Beatriz Lima',
    grade: '3º Ano Médio',
    riskScore: 12,
    status: 'Estável',
    kpis: { attendance: '98%', average: '8.9', financial: 'Em dia' },
    ai_analysis:
      'Alto engajamento. Padrão compatível com aprovação em vestibulares de ponta.'
  },
  {
    id: 4,
    name: 'Gabriel Nunes',
    grade: '8º Ano A',
    riskScore: 88,
    status: 'Risco Crítico',
    kpis: { attendance: '74%', average: '5.0', financial: '20 dias atraso' },
    ai_analysis:
      'Sinais combinados de evasão: faltas recorrentes, queda em matemática e atraso financeiro atípico no último mês.'
  },
  {
    id: 5,
    name: 'Ana Clara Pereira',
    grade: '2º Ano Médio',
    riskScore: 66,
    status: 'Atenção',
    kpis: { attendance: '88%', average: '6.4', financial: 'Em dia' },
    ai_analysis:
      'Queda de desempenho em exatas nas últimas avaliações e redução de participação em atividades de reforço.'
  },
  {
    id: 6,
    name: 'Rafael Costa',
    grade: '1º Ano Médio',
    riskScore: 52,
    status: 'Atenção',
    kpis: { attendance: '91%', average: '6.1', financial: '8 dias atraso' },
    ai_analysis:
      'Padrão de oscilação acadêmica em matemática e início de atraso financeiro leve; sugerida mentoria preventiva.'
  },
  {
    id: 7,
    name: 'Juliana Martins',
    grade: '7º Ano C',
    riskScore: 14,
    status: 'Estável',
    kpis: { attendance: '97%', average: '8.7', financial: 'Em dia' },
    ai_analysis:
      'Rotina consistente, evolução contínua e alta participação em projetos; perfil acadêmico estável e colaborativo.'
  },
  {
    id: 8,
    name: 'Pedro Henrique',
    grade: '3º Ano Médio',
    riskScore: 84,
    status: 'Risco Crítico',
    kpis: { attendance: '76%', average: '5.4', financial: '18 dias atraso' },
    ai_analysis:
      'Queda acentuada em exatas, faltas consecutivas e atraso financeiro persistente elevam risco de evasão no trimestre.'
  },
  {
    id: 9,
    name: 'Larissa Melo',
    grade: '6º Ano B',
    riskScore: 44,
    status: 'Atenção',
    kpis: { attendance: '93%', average: '6.9', financial: 'Em dia' },
    ai_analysis:
      'Oscilação de notas em matemática e redução de engajamento no portal nas últimas duas semanas.'
  },
  {
    id: 10,
    name: 'Thiago Almeida',
    grade: '9º Ano A',
    riskScore: 9,
    status: 'Estável',
    kpis: { attendance: '99%', average: '9.1', financial: 'Em dia' },
    ai_analysis:
      'Desempenho acadêmico excelente, presença alta e comportamento financeiro regular da família.'
  }
])

const teachersData = reactive([
  {
    id: 1,
    name: 'Fernanda Lima',
    discipline: 'Ciências da Natureza',
    burnoutRisk: 'alto',
    burnoutScore: 82,
    metrics: '12 diários atrasados · 450 alunos',
    ai_insight: 'Sobrecarga detectada. Tempo de correção subiu 40% e houve queda média de desempenho em duas turmas.'
  },
  {
    id: 2,
    name: 'Ricardo Torres',
    discipline: 'Matemática',
    burnoutRisk: 'baixo',
    burnoutScore: 33,
    metrics: '2 diários atrasados · 310 alunos',
    ai_insight: 'Ritmo de correção estável e alto engajamento em reforço. Perfil saudável de carga de trabalho.'
  },
  {
    id: 3,
    name: 'Patrícia Gomes',
    discipline: 'Linguagens',
    burnoutRisk: 'alto',
    burnoutScore: 74,
    metrics: '9 diários atrasados · 390 alunos',
    ai_insight: 'Padrão de desgaste crescente após assumir turmas extras. Recomendada redistribuição parcial de carga.'
  }
])

const financeData = reactive([
  {
    id: 1,
    nome_responsavel: 'Família Souza',
    aluno: 'Mariana Souza',
    status: 'Atraso Anômalo',
    debt: 'R$ 1.240,00',
    ai_recommendation: 'Primeiro atraso em 2 anos. Sugestão: abordagem empática, possível perda de emprego da família.'
  },
  {
    id: 2,
    nome_responsavel: 'Família Almeida',
    aluno: 'Lucas Almeida',
    status: 'Atraso Padrão',
    debt: 'R$ 680,00',
    ai_recommendation: 'Histórico recorrente de atraso entre os dias 8 e 12. Notificação preventiva tende a resolver.'
  },
  {
    id: 3,
    nome_responsavel: 'Família Costa',
    aluno: 'Ana Costa',
    status: 'Atraso Anômalo',
    debt: 'R$ 980,00',
    ai_recommendation: 'Padrão fora da curva com queda abrupta de pagamento. Priorizar acordo para evitar evasão financeira.'
  }
])

const settings = reactive({
  autoWhatsapp: true,
  riskSensitivity: false,
  erpSync: true
})

const isAILoading = ref(true)

onMounted(() => {
  setTimeout(() => {
    isAILoading.value = false
  }, 2500)
})

const kpiCards = computed(() => [
  {
    id: 'frequency',
    label: 'Frequência Geral',
    value: `${atlasData.kpis.general_frequency.toFixed(1).replace('.', ',')}%`
  },
  {
    id: 'average',
    label: 'Média Acadêmica',
    value: atlasData.kpis.academic_average.toFixed(1).replace('.', ',')
  },
  {
    id: 'overdue',
    label: 'Boletos Vencidos',
    value: `${atlasData.kpis.overdue_bills}`
  },
  {
    id: 'students',
    label: 'Alunos Ativos',
    value: atlasData.kpis.total_active_students.toLocaleString('pt-BR')
  }
])

const formattedDate = computed(() => {
  const [year, month, day] = atlasData.school_info.current_date.split('-')
  const date = new Date(Number(year), Number(month) - 1, Number(day))
  return date.toLocaleDateString('pt-BR', {
    weekday: 'long',
    day: '2-digit',
    month: 'long',
    year: 'numeric'
  })
})

const pageHeader = computed(() => {
  if (currentTab.value === 'dashboard') {
    return {
      title: `Bom dia, Diretor ${atlasData.school_info.manager_name}!`,
      subtitle: `${atlasData.school_info.name} · Vice-Diretor Digital preditivo`
    }
  }

  if (currentTab.value === 'alunos') {
    return {
      title: 'Gestão de Alunos',
      subtitle: 'Monitoramento preditivo e risco de evasão'
    }
  }

  if (currentTab.value === 'professores') {
    return {
      title: 'Corpo Docente',
      subtitle: 'Saúde operacional, carga de trabalho e risco de burnout'
    }
  }

  if (currentTab.value === 'financeiro') {
    return {
      title: 'Financeiro',
      subtitle: 'Cobrança inteligente orientada por padrões preditivos'
    }
  }

  return {
    title: 'Configurações',
    subtitle: 'Parâmetros e automações do Vice-Diretor Digital'
  }
})

const tabClass = (tab) => {
  if (currentTab.value === tab) return 'bg-cyan-500/20 font-medium text-cyan-300 ring-1 ring-cyan-400/30'
  return 'text-slate-300 hover:bg-slate-800'
}

const categoryBadgeClass = (category) => {
  if (category === 'Evasão') return 'bg-rose-100 text-rose-700'
  if (category === 'Desempenho') return 'bg-blue-100 text-blue-700'
  if (category === 'RH / Docente') return 'bg-purple-100 text-purple-700'
  return 'bg-slate-100 text-slate-700'
}

const riskBadgeClass = (score) => {
  if (score > 80) return 'bg-red-100 text-red-700'
  if (score > 50) return 'bg-amber-100 text-amber-700'
  if (score < 20) return 'bg-emerald-100 text-emerald-700'
  return 'bg-slate-100 text-slate-700'
}

const filteredStudents = computed(() => {
  if (currentFilter.value === 'Todos') return studentsData

  if (currentFilter.value === 'Risco Crítico') {
    return studentsData.filter((student) => student.status === 'Risco Crítico')
  }

  if (currentFilter.value === 'Queda em Exatas') {
    return studentsData.filter((student) => {
      const analysis = student.ai_analysis.toLowerCase()
      return analysis.includes('exatas') || analysis.includes('matemática') || analysis.includes('matematica')
    })
  }

  if (currentFilter.value === 'Alerta Financeiro') {
    return studentsData.filter((student) => student.kpis.financial !== 'Em dia')
  }

  return studentsData
})

const filterPillClass = (filter) => {
  if (currentFilter.value === filter) return 'bg-slate-900 text-white'
  return 'bg-white border border-slate-200 text-slate-600 hover:bg-slate-50'
}

const regularSimulationOptions = [
  { value: 'none', label: 'Sem ação' },
  { value: 'scholarship_10', label: 'Conceder bolsa de 10%' },
  { value: 'payment_plan', label: 'Acordo de parcelamento' }
]

const stableSimulationOptions = [
  { value: 'none', label: 'Manter acompanhamento' },
  { value: 'mentorship_program', label: 'Convidar para Programa de Monitoria' },
  { value: 'olympiad_challenge', label: 'Oferecer desafio extra (Olimpíadas)' }
]

const simulatedRiskMap = {
  1: { none: 85, scholarship_10: 28, payment_plan: 20 },
  2: { none: 60, scholarship_10: 48, payment_plan: 35 },
  3: { none: 12, mentorship_program: 9, olympiad_challenge: 8 }
}

const riskBreakdownBySimulation = {
  1: {
    none: [
      { label: 'Faltas recentes', value: 40 },
      { label: 'Sinal financeiro', value: 35 },
      { label: 'Queda em exatas', value: 10 }
    ],
    scholarship_10: [
      { label: 'Faltas recentes', value: 14 },
      { label: 'Sinal financeiro', value: 6 },
      { label: 'Queda em exatas', value: 8 }
    ],
    payment_plan: [
      { label: 'Faltas recentes', value: 10 },
      { label: 'Sinal financeiro', value: 2 },
      { label: 'Queda em exatas', value: 8 }
    ]
  },
  2: {
    none: [
      { label: 'Queda de notas', value: 30 },
      { label: 'Sinal financeiro', value: 12 },
      { label: 'Baixo acesso ao portal', value: 18 }
    ],
    scholarship_10: [
      { label: 'Queda de notas', value: 24 },
      { label: 'Sinal financeiro', value: 7 },
      { label: 'Baixo acesso ao portal', value: 17 }
    ],
    payment_plan: [
      { label: 'Queda de notas', value: 18 },
      { label: 'Sinal financeiro', value: 3 },
      { label: 'Baixo acesso ao portal', value: 14 }
    ]
  }
}

const retentionIndicatorsBySimulation = {
  3: {
    none: [
      { label: 'Engajamento Acadêmico', value: 94 },
      { label: 'Saúde Financeira', value: 98 },
      { label: 'Frequência', value: 96 }
    ],
    mentorship_program: [
      { label: 'Engajamento Acadêmico', value: 97 },
      { label: 'Saúde Financeira', value: 98 },
      { label: 'Frequência', value: 96 }
    ],
    olympiad_challenge: [
      { label: 'Engajamento Acadêmico', value: 99 },
      { label: 'Saúde Financeira', value: 98 },
      { label: 'Frequência', value: 97 }
    ]
  }
}

const isStableSelected = computed(() => selectedStudent.value?.status === 'Estável')

const simulationOptions = computed(() => {
  return isStableSelected.value ? stableSimulationOptions : regularSimulationOptions
})

const displayedRiskScore = computed(() => {
  if (!selectedStudent.value) return 0

  const studentSimulation = simulatedRiskMap[selectedStudent.value.id]
  if (!studentSimulation) return selectedStudent.value.riskScore

  return studentSimulation[selectedSimulation.value] ?? selectedStudent.value.riskScore
})

const displayedRiskStatus = computed(() => {
  if (displayedRiskScore.value > 80) return 'Risco Crítico'
  if (displayedRiskScore.value > 50) return 'Atenção'
  if (displayedRiskScore.value < 20) return 'Estável'
  return 'Monitorar'
})

const riskPanelTitle = computed(() => {
  return isStableSelected.value ? 'Indicadores de Retenção' : 'Composição do risco'
})

const riskStatusTagClass = computed(() => {
  if (displayedRiskStatus.value === 'Risco Crítico') return 'bg-rose-500/20 text-rose-400'
  if (displayedRiskStatus.value === 'Atenção') return 'bg-amber-500/20 text-amber-400'
  if (displayedRiskStatus.value === 'Estável') return 'bg-emerald-500/20 text-emerald-400'
  return 'bg-cyan-500/20 text-cyan-300'
})

const riskBreakdownItems = computed(() => {
  if (!selectedStudent.value) return []

  const studentData = isStableSelected.value
    ? retentionIndicatorsBySimulation[selectedStudent.value.id]
    : riskBreakdownBySimulation[selectedStudent.value.id]

  if (!studentData) {
    if (isStableSelected.value) {
      return [
        { label: 'Engajamento Acadêmico', value: 94 },
        { label: 'Saúde Financeira', value: 98 },
        { label: 'Frequência', value: 96 }
      ]
    }

    const base = displayedRiskScore.value
    const finance = Math.max(5, Math.round(base * 0.35))
    const attendance = Math.max(5, Math.round(base * 0.4))
    const performance = Math.max(5, base - finance - attendance)
    return [
      { label: 'Faltas recentes', value: attendance },
      { label: 'Sinal financeiro', value: finance },
      { label: 'Queda em exatas', value: performance }
    ]
  }

  return studentData[selectedSimulation.value] ?? studentData.none ?? []
})

const generatedCareMessage = computed(() => {
  if (!selectedStudent.value) return ''

  if (isStableSelected.value) {
    return `Olá família, ${selectedStudent.value.name} teve um excelente desempenho recente e gostaríamos de reconhecer esse resultado. Estamos convidando a estudante para novas oportunidades de protagonismo acadêmico.`
  }

  return `Olá família da ${selectedStudent.value.name}, notamos algumas ausências recentes e gostaríamos de agendar um café para conversar sobre como podemos apoiar o desenvolvimento acadêmico da(o) estudante com acolhimento e parceria.`
})

const copyCareMessage = async () => {
  if (!generatedCareMessage.value) return

  try {
    await navigator.clipboard.writeText(generatedCareMessage.value)
    copiedMessage.value = true
    setTimeout(() => {
      copiedMessage.value = false
    }, 1800)
  } catch {
    copiedMessage.value = false
  }
}

watch(
  () => selectedStudent.value,
  () => {
    showAICopilot.value = false
    copiedMessage.value = false
    selectedSimulation.value = 'none'
  }
)

watch(
  () => simulationOptions.value,
  (options) => {
    if (!options.some((option) => option.value === selectedSimulation.value)) {
      selectedSimulation.value = options[0]?.value ?? 'none'
    }
  }
)
</script>

<style scoped>
:global(body) {
  margin: 0;
  font-family: 'Inter', 'Segoe UI', sans-serif;
  background-color: rgb(248 250 252);
}

.alert-action-btn {
  height: 2.5rem;
  padding-left: 1rem;
  padding-right: 1rem;
  white-space: nowrap;
  border-radius: 0.75rem;
  background-color: rgb(15 23 42);
  color: white;
  font-size: 0.875rem;
  font-weight: 600;
  transition: background-color 0.2s;
}

.alert-action-btn:hover {
  background-color: rgb(51 65 85);
}
</style>
