# 📐 FormatoLatex - LaTeX Renderer for Java Swing

<div align="center">

![Java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=java&logoColor=white)
![Swing](https://img.shields.io/badge/Swing-007396?style=for-the-badge&logo=java&logoColor=white)
![LaTeX](https://img.shields.io/badge/LaTeX-008080?style=for-the-badge&logo=latex&logoColor=white)
![Version](https://img.shields.io/badge/Version-1.0-blue?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

Una librería Java elegante y poderosa para renderizar fórmulas matemáticas LaTeX en aplicaciones Swing

[📖 Documentación](#-documentación) • [🚀 Instalación](#-instalación) • [💡 Ejemplos](#-ejemplos) • [🎥 Demo](#-demo)

</div>

---

## 🌟 Descripción

**FormatoLatex** es una librería de utilidad que permite integrar fórmulas matemáticas LaTeX de manera sencilla en aplicaciones Java Swing. Construida sobre la base de JLaTeXMath, esta librería ofrece una API intuitiva para:

- ✨ Renderizar fórmulas matemáticas complejas en componentes Swing
- 🖼️ Exportar fórmulas como imágenes PNG de alta calidad
- 🎨 Personalizar colores y estilos de renderizado
- 📊 Mostrar matrices y expresiones matemáticas en ventanas independientes
- 🔧 Integración simple con proyectos existentes

Esta librería surge de la necesidad de tener métodos que faciliten la visualización de fórmulas matemáticas en un formato adecuado, permitiendo a los usuarios centrarse en el contenido mientras la biblioteca se encarga de la renderización en formato LaTeX.

## 🚀 Instalación

### Requisitos
- Librería [JLaTeXMath](https://github.com/opencollab/jlatexmath). Enlace al [JAR](https://mvnrepository.com/artifact/org.scilab.forge/jlatexmath/1.0.7)

### Importar JAR en tu proyecto

1. **Descarga archivo JAR (tanto el de formatolatex como el JLatexMath**
2. **Agrega ambos JAR a tu proyecto:**

#### Para NetBeans:
```
Click derecho en el proyecto → Properties → Libraries → Modulepath → Add JAR/Folder
```

## 📚 Documentación

### Arquitectura de la Clase

La clase `FormatoLatex` está diseñada siguiendo principios de programación limpia y patrones de utilidad:

```java
public final class FormatoLatex {
    // Métodos estáticos para facilitar el uso
    // Sin necesidad de instanciar la clase
}
```

### Javadoc

> 📄 **[Documentación Javadoc](https://fergmlx.github.io/libreria-formato-latex)**

### 🔧 Métodos Principales

#### 1. Renderizado de Fórmulas como Imágenes

```java
// Renderizado básico con colores predeterminados
public static void renderizarFormula(String formulaLatex, float texSize, String ruta)

// Renderizado con colores personalizados
public static void renderizarFormula(String formulaLatex, float texSize, String ruta, 
                                   Color background, Color foreground)
```

**Parámetros:**
- `formulaLatex`: Expresión matemática en formato LaTeX
- `texSize`: Tamaño del texto (recomendado: 16-24)
- `ruta`: Ruta completa donde guardar el archivo PNG
- `background`: Color de fondo (opcional)
- `foreground`: Color del texto (opcional)

**Características:**
- ✅ Validación de archivos existentes con confirmación
- ✅ Manejo de errores con mensajes informativos
- ✅ Calidad de imagen optimizada (TYPE_INT_ARGB)
- ✅ Márgenes automáticos para mejor visualización

#### 2. Integración con Componentes Swing

```java
// Establecer fórmula en JLabel existente
public static void establecerMathTex(JLabel label, String formulaLatex, float textSize)

// Crear nuevo JLabel con fórmula
public static JLabel crearMathTex(String formulaLatex, float textSize)

// Para texto normal formateado
public static void establecerTex(JLabel label, String tex, float texSize)
public static JLabel crearTex(String text, float textSize)
```

**Validaciones implementadas:**
- Control de excepciones durante el renderizado
- Limpieza automática del texto previo en JLabel
- Configuración automática de iconos

#### 3. Ventanas de Visualización

```java
// Mostrar fórmula en ventana independiente
public static void mostrarFormulaEnVentana(String formulaLatex, float textSize)

// Mostrar texto formateado en ventana
public static void mostrarTexEnVentana(String text, float textSize)

// Mostrar matriz en formato LaTeX
public static void mostrarMatrizVentana(String[][] matriz, float tamaño)
```

**Características de las ventanas:**
- 📐 Tamaño optimizado (400x200 pixels)
- 🎯 Centrado automático en pantalla
- 🔄 Disposición automática al cerrar
- 📊 Alineación centrada del contenido

### 🎨 Variables y Configuraciones

#### Estilos de Renderizado
```java
TeXConstants.STYLE_DISPLAY  // Estilo matemático completo
TeXConstants.ALIGN_CENTER   // Alineación centrada
TeXConstants.UNIT_PIXEL     // Unidad de medida en píxeles
```

#### Configuraciones de Imagen
```java
BufferedImage.TYPE_INT_ARGB  // Soporte para transparencia
Insets(5, 5, 5, 5)          // Márgenes uniformes
```

## 💡 Ejemplos de Uso

### Ejemplo 1: Renderizar Ecuación Cuadrática
```java
import formatolatex.FormatoLatex;

public class EjemploBasico {
    public static void main(String[] args) {
        String ecuacion = "x = \\frac{-b \\pm \\sqrt{b^2 - 4ac}}{2a}";
        
        // Guardar como imagen PNG
        FormatoLatex.renderizarFormula(ecuacion, 20f, "ecuacion_cuadratica.png");
        
        // Mostrar en ventana
        FormatoLatex.mostrarFormulaEnVentana(ecuacion, 20f);
    }
}
```

### Ejemplo 2: Integración con JLabel
```java
import formatolatex.FormatoLatex;
import javax.swing.*;

public class IntegracionSwing {
    public static void main(String[] args) {
        JFrame frame = new JFrame("Fórmulas Matemáticas");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setLayout(new FlowLayout());
        
        // Crear JLabel con fórmula
        JLabel etiqueta1 = FormatoLatex.crearMathTex("E = mc^2", 18f);
        frame.add(etiqueta1);
        
        // Modificar JLabel existente
        JLabel etiqueta2 = new JLabel();
        FormatoLatex.establecerMathTex(etiqueta2, "\\sum_{i=1}^{n} i = \\frac{n(n+1)}{2}", 16f);
        frame.add(etiqueta2);
        
        frame.pack();
        frame.setVisible(true);
    }
}
```

### Ejemplo 3: Matriz Matemática
```java
import formatolatex.FormatoLatex;

public class EjemploMatriz {
    public static void main(String[] args) {
        String[][] matriz = {
            {"a_{11}", "a_{12}", "a_{13}"},
            {"a_{21}", "a_{22}", "a_{23}"},
            {"a_{31}", "a_{32}", "a_{33}"}
        };
        
        FormatoLatex.mostrarMatrizVentana(matriz, 18f);
    }
}
```

### Ejemplo 4: Colores Personalizados
```java
import formatolatex.FormatoLatex;
import java.awt.Color;

public class EjemploColores {
    public static void main(String[] args) {
        String formula = "\\int_{-\\infty}^{\\infty} e^{-x^2} dx = \\sqrt{\\pi}";
        
        // Fondo negro con texto blanco
        FormatoLatex.renderizarFormula(formula, 22f, "integral_personalizada.png", 
                                     Color.BLACK, Color.WHITE);
        
        // Fondo azul con texto amarillo
        FormatoLatex.renderizarFormula(formula, 22f, "integral_colorida.png", 
                                     Color.BLUE, Color.YELLOW);
    }
}
```

## 🎯 Casos de Uso Comunes

### 📊 Aplicaciones Educativas
- Generadores de ejercicios matemáticos
- Plataformas de aprendizaje interactivo
- Editores de contenido académico

### 🔬 Software Científico
- Calculadoras científicas avanzadas
- Simuladores matemáticos
- Herramientas de análisis numérico

### 📈 Aplicaciones de Visualización
- Generadores de reportes con fórmulas
- Dashboards científicos
- Presentaciones técnicas

## 🛠️ Mejores Prácticas

### ❌ Evitar
```java
// Tamaños muy pequeños o muy grandes
FormatoLatex.renderizarFormula(formula, 8f, ruta);   // ❌ Muy pequeño
FormatoLatex.renderizarFormula(formula, 100f, ruta); // ❌ Muy grande

// Fórmulas LaTeX inválidas sin validación
FormatoLatex.renderizarFormula("\\invalid{formula", 18f, ruta); // ❌ Sintaxis incorrecta
```

Un par de recursos sobre LaTeX:
> 📄 **[Manual de LaTeX](https://manualdelatex.com/tutoriales/ecuaciones)**

> 📗 **[Introducción a LaTeX](https://www.ugr.es/~mmartins/material/latex_basico.pdf)** (Recomendable ver sección *Comandos y entornos*)

## 🎥 Video explicativo

[![Ver demostración en YouTube](https://img.shields.io/badge/YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://youtu.be/PtQnJSb-3n0?si=8PbGDUQEFc0F-8jH)

## 👥 Créditos

- [JLaTeXMath](https://github.com/opencollab/jlatexmath) por la base de renderizado LaTeX
<div align="center">
  <table>
    <tr>
      <td align="center">
        <a href="https://github.com/fergmlx">
          <img src="https://github.com/fergmlx.png" width="100px;" alt=""/>
          <br />
          <sub><b>Luis Fernando González Miguel</b></sub>
        </a>
        <br />
        <sub>Miembro del equipo</sub>
      </td>
      <!-- Añade más miembros del equipo aquí siguiendo el mismo formato -->
      <td align="center">
        <a href="https://github.com/JonathanRene">
          <img src="https://github.com/JonathanRene.png" width="100px;" alt=""/>
          <br />
          <sub><b>Jonathan Rene Cruz Gutiérrez</b></sub>
        </a>
        <br />
        <sub>Miembro del equipo</sub>
      </td>
    </tr>
  </table>
</div>
