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

**FormatoLatex** es una librería de utilidad especializada que permite integrar fórmulas matemáticas LaTeX de manera sencilla y elegante en aplicaciones Java Swing. Construida sobre la base de JLaTeXMath, esta librería ofrece una API intuitiva para:

- ✨ Renderizar fórmulas matemáticas complejas en componentes Swing
- 🖼️ Exportar fórmulas como imágenes PNG de alta calidad
- 🎨 Personalizar colores y estilos de renderizado
- 📊 Mostrar matrices y expresiones matemáticas en ventanas independientes
- 🔧 Integración simple con proyectos existentes

Esta librería surge de la necesidad de tener métodos que faciliten la visualización de fórmulas matemáticas en un formato adecuado, permitiendo a los usuarios centrarse en el contenido mientras la biblioteca se encarga de la renderización en formato LaTeX.

## 🚀 Instalación

### Requisitos
- Java 8 o superior
- [JLaTeXMath](https://github.com/opencollab/jlatexmath) library

### Método 1: Importar JAR en tu proyecto

1. **Descarga el archivo JAR** desde la sección de releases
2. **Agrega el JAR a tu proyecto:**

#### Para IntelliJ IDEA:
```
File → Project Structure → Modules → Dependencies → + → JARs or directories
```

#### Para Eclipse:
```
Right-click project → Properties → Java Build Path → Libraries → Add JARs
```

#### Para NetBeans:
```
Right-click project → Properties → Libraries → Add JAR/Folder
```

### Método 2: Usando Maven (próximamente)
```xml
<dependency>
    <groupId>com.formatolatex</groupId>
    <artifactId>formato-latex</artifactId>
    <version>1.0.0</version>
</dependency>
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

### ✅ Recomendaciones
```java
// Usar tamaños de texto apropiados
FormatoLatex.renderizarFormula(formula, 18f, ruta);  // ✅ Óptimo para pantalla
FormatoLatex.renderizarFormula(formula, 24f, ruta);  // ✅ Óptimo para impresión

// Validar rutas antes de renderizar
File directorio = new File("output");
if (!directorio.exists()) {
    directorio.mkdirs();
}
```

### ❌ Evitar
```java
// Tamaños muy pequeños o muy grandes
FormatoLatex.renderizarFormula(formula, 8f, ruta);   // ❌ Muy pequeño
FormatoLatex.renderizarFormula(formula, 100f, ruta); // ❌ Muy grande

// Fórmulas LaTeX inválidas sin validación
FormatoLatex.renderizarFormula("\\invalid{formula", 18f, ruta); // ❌ Sintaxis incorrecta
```

## 🎥 Demo

> 📹 **[Ver video demostrativo en YouTube](https://youtube.com/watch?v=YOUR_VIDEO_ID)**

El video incluye:
- Instalación paso a paso
- Ejemplos de uso en tiempo real
- Integración con diferentes IDEs
- Casos de uso avanzados

## 🤝 Contribución

¡Las contribuciones son bienvenidas! Si deseas mejorar la librería:

1. Fork el repositorio
2. Crea una rama para tu feature (`git checkout -b feature/AmazingFeature`)
3. Commit tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abre un Pull Request

## 📝 Licencia

Distribuido bajo la licencia MIT. Ver `LICENSE` para más información.

## 👥 Autores

- **Fer** - *Desarrollador Principal* - [@fergmlx](https://github.com/fergmlx)
- **Jonathan** - *Colaborador* - Documentación y testing

## 🙏 Agradecimientos

- [JLaTeXMath](https://github.com/opencollab/jlatexmath) por la base de renderizado LaTeX
- Comunidad Java por el feedback y sugerencias
- Contribuidores del proyecto

---

<div align="center">

**¿Te gusta FormatoLatex? ¡Dale una ⭐ al repositorio!**

[🐛 Reportar Bug](../../issues) • [💡 Solicitar Feature](../../issues) • [📧 Contacto](mailto:your-email@example.com)

</div>
