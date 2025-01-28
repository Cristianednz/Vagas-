# Vagas-
bash
src/
├── components/
│   ├── admin/
│   │   ├── CandidateStatus.jsx
│   │   ├── Dashboard.jsx
│   │   └── JobManagement.jsx
│   ├── candidate/
│   │   ├── CandidateForm.jsx
│   │   └── ExperienceForm.jsx
│   ├── shared/
│   │   ├── StatusBadge.jsx
│   │   └── SourceBadge.jsx
│   ├── ui/
│   │   └── [componentes shadcn/ui]
│   └── JobMatchingApp.jsx
├── utils/
│   ├── constants.js
│   └── helpers.js
├── styles/
│   └── globals.css
├── App.jsx
└── main.jsx
javascript
// src/utils/constants.js
export const SOURCE_OPTIONS = [
  { value: 'LINKEDIN', label: 'LinkedIn' },
  { value: 'INDEED', label: 'Indeed' },
  { value: 'SITE_EMPRESA', label: 'Site da Empresa' },
  { value: 'INDICACAO', label: 'Indicação' },
  { value: 'INSTAGRAM', label: 'Instagram' },
  { value: 'FACEBOOK', label: 'Facebook' },
  { value: 'VAGAS_COM', label: 'Vagas.com' },
  { value: 'GUPY', label: 'Gupy' },
  { value: 'OUTROS', label: 'Outros' }
];

export const STATUS_OPTIONS = [
  { value: 'NOVO', label: 'Novo' },
  { value: 'ANÁLISE', label: 'Em Análise' },
  { value: 'ENTREVISTA', label: 'Entrevista' },
  { value: 'TESTE', label: 'Teste' },
  { value: 'APROVADO', label: 'Aprovado' },
  { value: 'REPROVADO', label: 'Reprovado' },
  { value: 'DESISTENTE', label: 'Desistente' }
];

export const WITHDRAWAL_REASONS = [
  { value: 'OUTRA_PROPOSTA', label: 'Aceitou outra proposta' },
  { value: 'SALARIO', label: 'Incompatibilidade salarial' },
  { value: 'BENEFICIOS', label: 'Incompatibilidade de benefícios' },
  { value: 'LOCALIZACAO', label: 'Localização/Deslocamento' },
  { value: 'HORARIO', label: 'Incompatibilidade de horário' },
  { value: 'MODELO_TRABALHO', label: 'Modelo de trabalho' },
  { value: 'SEM_RETORNO', label: 'Sem retorno do candidato' },
  { value: 'OUTROS', label: 'Outros motivos' }
];

export const COLORS = {
  navy: {
    50: '#f0f5fa',
    100: '#e1eaf4',
    200: '#c2d5e9',
    300: '#94b5d7',
    400: '#6690c3',
    500: '#446fa6',
    600: '#335687',
    700: '#2a466f',
    800: '#25395c',
    900: '#223050',
  }
};


javascript
// src/utils/helpers.js
export const formatDate = (date) => {
  if (!date) return '';
  return new Date(date).toLocaleDateString();
};

export const getStatusColor = (status) => {
  const colors = {
    NOVO: 'gray',
    'ANÁLISE': 'navy',
    ENTREVISTA: 'yellow',
    TESTE: 'purple',
    APROVADO: 'green',
    REPROVADO: 'red',
    DESISTENTE: 'orange'
  };
  return colors[status] || 'gray';
};

export const calculateConversionRate = (approved, total) => {
  if (!total) return '0.0';
  return ((approved / total) * 100).toFixed(1);
};


Agora, vou compartilhar os componentes compartilhados:

jsx
// src/components/shared/StatusBadge.jsx
import React from 'react';
import { getStatusColor } from '@/utils/helpers';

export const StatusBadge = ({ status }) => {
  const color = getStatusColor(status);
  
  return (
    <span className={`px-3 py-1 rounded-full text-sm font-medium
      bg-${color}-100 text-${color}-700`}>
      {status}
    </span>
  );
};


jsx
// src/components/shared/SourceBadge.jsx
import React from 'react';
import { SOURCE_OPTIONS } from '@/utils/constants';

export const SourceBadge = ({ source }) => {
  const sourceOption = SOURCE_OPTIONS.find(opt => opt.value === source);
  
  return (
    <span className="px-3 py-1 rounded-full text-sm font-medium bg-navy-100 text-navy-700">
      {sourceOption?.label || 'Fonte não informada'}
    </span>
  );
};
