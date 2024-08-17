# l-gica-de-predicados-
El programa comienza definiendo un objeto enfermedades que contiene una lista de enfermedades y sus respectivos síntoma

// Definición de enfermedades y sus síntomas
const enfermedades = {
    "Gripe": ["fiebre", "tos", "dolor de garganta", "fatiga"],
    "Covid-19": ["fiebre", "tos", "dificultad para respirar", "pérdida del olfato", "pérdida del gusto"],
    "Resfriado común": ["congestión nasal", "tos", "dolor de cabeza", "estornudos"],
    "Alergia": ["estornudos", "picazón en los ojos", "congestión nasal", "erupción cutánea"],
    "Gastritis": ["dolor abdominal", "náuseas", "vómitos", "ardor estomacal"],
};

// Función para diagnosticar la enfermedad en base a los síntomas proporcionados
function diagnosticar(sintomas) {
    let diagnostico = [];

    for (const [enfermedad, sintomasEnfermedad] of Object.entries(enfermedades)) {
        const coincidencias = sintomas.filter(sintoma => sintomasEnfermedad.includes(sintoma));
        
        // Si todos los síntomas coinciden, agregar la enfermedad al diagnóstico
        if (coincidencias.length === sintomas.length) {
            diagnostico.push(enfermedad);
        }
    }

    // Si no se encuentra una coincidencia exacta, se puede considerar la enfermedad con más síntomas coincidentes
    if (diagnostico.length === 0) {
        let maxCoincidencias = 0;
        let posibleEnfermedad = "No se pudo diagnosticar una enfermedad con los síntomas proporcionados.";

        for (const [enfermedad, sintomasEnfermedad] of Object.entries(enfermedades)) {
            const coincidencias = sintomas.filter(sintoma => sintomasEnfermedad.includes(sintoma));
            
            if (coincidencias.length > maxCoincidencias) {
                maxCoincidencias = coincidencias.length;
                posibleEnfermedad = enfermedad;
            }
        }

        diagnostico.push(posibleEnfermedad);
    }

    return diagnostico;
}

// Ejemplo de uso
const sintomasUsuario = ["fiebre", "tos", "dolor de garganta", "fatiga"];
const resultado = diagnosticar(sintomasUsuario);

console.log("Diagnóstico basado en los síntomas:", resultado);
