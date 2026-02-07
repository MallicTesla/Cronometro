<template>
  <div class="cronometro-display">
    <!-- Tiempo principal -->
    <div class="tiempo-principal">
      {{ cronometroStore.tiempoFormateado }}
    </div>

    <!-- Tiempo de la marca actual (EN VIVO) -->
    <div class="tiempo-marca-actual"> {{ cronometroStore.tiempoMarcaActualFormateado }}
    </div>

    <!-- Estadísticas -->
    <div v-if="cronometroStore.totalMarcas > 0" class="estadisticas">
      <div class="estadistica-item">
        <div class="estadistica-label">
          {{ $t('cronometro.totalMarcas') }}
        </div>
        <div class="estadistica-valor">
          {{ cronometroStore.totalMarcas }}
        </div>
      </div>

      <div class="estadistica-separador"></div>

      <div class="estadistica-item">
        <div class="estadistica-label">
          {{ $t('cronometro.promedioMarcas') }}
        </div>
        <div class="estadistica-valor">
          {{ cronometroStore.promedioFormateado }}
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { useCronometroStore } from 'src/stores/cronometro'

const cronometroStore = useCronometroStore()
</script>

<style scoped>
.cronometro-display {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 1rem;
  gap: 0.6rem;
  width: 100%;
}

/* Reloj principal */
.tiempo-principal {
  font-size: clamp(3.5rem, 12vw, 5rem);
  font-weight: 700;
  color: var(--color-texto-blanco);
  font-variant-numeric: tabular-nums;
  text-shadow: 0 4px 12px rgba(0, 63, 131, 0.3);
  line-height: 1;
  letter-spacing: -1px;
}

/* Reloj secundario (marca actual) */
.tiempo-marca-actual {
  font-size: clamp(2.4rem, 5vw, 1.8rem);
  font-weight: 600;
  color: var(--color-azul-claro);
  font-variant-numeric: tabular-nums;
  opacity: 0.85;
  letter-spacing: 0.5px;
}

/* Estadísticas */
.estadisticas {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 1.5rem;
  padding: 0.5rem 1.25rem;
  margin-top: 0.4rem;
  background: rgba(255, 255, 255, 0.1);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 50px;
}

.estadistica-item {
  display: flex;
  flex-direction: row;
  align-items: baseline;
  gap: 0.5rem;
}

.estadistica-label {
  font-size: 0.7rem;
  color: var(--color-azul-claro);
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: 600;
}

.estadistica-valor {
  font-size: 1rem;
  font-weight: 700;
  color: var(--color-texto-blanco);
  font-variant-numeric: tabular-nums;
}

.estadistica-separador {
  width: 1px;
  height: 12px;
  background: rgba(255, 255, 255, 0.2);
}
</style>
