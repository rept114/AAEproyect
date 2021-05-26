**PROYECTO FINAL**

TÓPICOS DE FÍSICA

**Equipo:**

Aguilar Morales Alma Delfina

Zamora Gámez Jesús Armando

Pereo Torres Erik Rodrigo

**Abstract**

En el presente proyecto se muestra el trabajo final del semestre, siendo este el resultado de los aprendizajes obtenidos a lo largo de las clases de Tópicos de Física. En dicho proyecto se muestran elementos codificados con la finalidad de asimilarse a la realidad, tales como modelos de luz y movimiento.

**Introducción**

Tradicionalmente, las personas con cierto conocimiento de programación son quienes se han ocupado de crear los shaders en Unity. Shader Graph da la posibilidad a los artistas y otros integrantes del equipo, gracias a que permite crear shaders muy fácilmente, tal como los que se presentan en el proyecto.

Para este proyecto se creó una escena en Unity donde se presentan los elementos solicitados para dicho trabajo en base a lo aprendido y aplicado en el transcurso del semestre:

-Modelo de agua con vertex shading

-Vegetación con vertex shading

-Modelo de luz custom

**Antecedentes**

Un shader es un pequeño programa que se ejecuta directamente en el procesador de la placa de video (GPU). Esto permite hacer efectos gráficos con muy poco impacto en el rendimiento. Las CPUs no están orientadas a gráficos, matemática de vectores, matrices, mientras que las GPUs sí, y además están pensadas para trabajar de forma paralela.

Básicamente exiten tres tipos de shaders:

Vertex Shaders: se ejecutan una vez por cada vértice que forma parte del elemento que se quiere renderizar. Permiten hacer efectos sobre los propios vértices, es decir, moverlos para hacer algún efecto de distorsión (aplicar una función trigonométrica como seno podría servir para simular las olas de un océano, por ejemplo). Su valor de retorno es la posición del vértice procesada.

Pixel Shaders (en OpenGL los llaman Fragment Shader): se ejecutan una vez por cada fragmento visible de la imagen (es decir, la cantidad de veces que se ejecuten depende de la vista de cámara, tamaño del objeto y otros factores más). Su valor de retorno es el color del pixel resultante. Con la ayuda de los vertex shaders, permiten hacer efectos vistosos como iluminación, cel shading, bump mapping, y una gran cantidad de filtros de post-procesamiento como desenfoque, profundidad de campo, desenfoque de movimiento, bloom, hdr, entre otros.

Geometry Shaders: se ejecutan por cada cara del modelo que se quiere renderizar. Tienen la particularidad que pueden crear nuevos vértices por lo que son muy útiles para generar efectos como pasto, pelo, sombras proyectadas, reflejos, etc.

**Desarrollo**

Como primer paso, se creó un documento en Unity, donde también creamos una escena para el trabajo y después de esto, se creó una carpeta para los Shaders necesarios. En esta carpeta se desarrollaron los Shaders de manera individual para posteriormente aplicarlos de manera conjunta a la escena.

Como primer elemento, trabajamos el agua, donde al no ser necesario utilizar Sprites, generamos un grafo universal. Al querer emular agua real, optamos por darle una apariencia transparente a la superficie para que, de esta manera, apareciera parcialmente el terreno conforme fuera aumentando la altura de este. En cuanto al movimiento, creamos un mapa de normales que nos permitiera controlar la fuerza para darle cierto aspecto natural conectándolo así con el vertex.

La ley de Lambert trata sobre la iluminancia de una superficie situada a una cierta distancia de una fuente de luz. Aplicando esto en nuestro código, en conjunto con el Albedo para el color, se hizo aplicación de la dirección de luz en nuestra escena según lo que consideramos que luciera realista. Se crearon los subgrafos correspondientes para la atenuación y el rebote de luces. Toon shading es una técnica de renderización no fotorrealista que hace que los modelos 3D parezcan planos. Como el shader toon requiere que cambiemos la forma en que se refleja la luz, es un problema, en su lugar necesitamos un modelo de iluminación personalizado. Para ello se aplicaron las configuraciones vistas en clase e hicimos uso del Ramp textura el cual hizo posible lograr un aspecto de toon shading.

Para el tema del césped, aplicamos las variables que nos permitieron controlar tanto la velocidad del viento como su intensidad para emular un aspecto natural dentro de la escena. Aplicando inicialmente el modelo en la escena, este se introduce de manera estática, sin movimiento, por lo que es necesario configurar el vértice y así conseguir el efecto de viento que buscamos. Empleamos un vector con el cual se reguló la fuerza del viento multiplicándolo por el tiempo, haciendo uso de un Tiling and offset. Para configurar la posición del ruido del vértice, aplicamos un Gradient Noise. Tras hacer las conexiones correspondientes, lo conectamos con el vertex position logrando el efecto resultante.

Se implementaron los shaders en la escena, desde el agua, hasta el viento, la luz, las plantas y árboles dentro de un terreno diseñado con mapa de normales y sus texturas correspondientes.

**Conclusiones**

Como resultado final logramos una escena con diferentes elementos simulando un ecosistema natural, donde en base a las configuraciones previamente mencionadas, se obtuvieron efectos bastante buenos que cumplen con lo solicitado para este trabajo. Pusimos en práctica nuestros conocimientos obtenidos a lo largo del semestre, y además nos vimos en la tarea de consultar en diversas fuentes para poder resolver dudas o dificultades que se presentaron a lo largo del proyecto.

**Resultado**

https://drive.google.com/drive/folders/1BWDHbmXisKzas6CjPvyxorWm3f2zTaxv?usp=sharing

**Referencias**

- Antonio Moon. (2019). Shaders (Ley de Lambert) y Cell Shading (Toon). 25/05/2021, de GitHub Sitio web: https://moonantonio.github.io/post/2019/dev/002/#:~:text=Cell%20Shader,los%20modelos%203D%20parezcan%20planos.&amp;text=Algunas%20implementaciones%20del%20shader%20Toon,(NdotL)%20a%20otro%20valor.
- Anónimo. (2018). RoyStan. Grass Shader. Recuperado de: https://roystan.net/articles/grass-shader.html
- Anónimo. (2018). RoyStan. Toon Shader. Recuperado de: https://roystan.net/articles/toon-shader.html
- Anónimo. (2021). Game Dev. Water Shader. Recuperado de: https://gamedev.stackexchange.com/questions/183143/need-to-generate-seamless-gradient-noise-texture-for-water-shader?noredirect=1&amp;lq=1
- Anónimo. (s.f.). Superficie de agua simulada con animación de caso-vértice. 25/05/2021, de programador clic Sitio web: https://programmerclick.com/article/82521837246/
- Creating water with shader graph in unity| 2D shader basics. (2020, 27 octubre). CGTubes. https://www.cgtutes.com/water-shader-graph-unity/
- Creating water with shader graph in unity| 2D shader basics. (2020, 27 octubre). CGTubes. https://www.cgtutes.com/water-shader-graph-unity/
- Creating water with shader graph in unity| 2D shader basics. (2020, 27 octubre). CGTubes. https://www.cgtutes.com/water-shader-graph-unity/
- Ilett, D. (2020, 5 abril). Stylised Water in Shader Graph and URP. Daniel Ilett: Games | Shaders | Tutorials. https://danielilett.com/2020-04-05-tut5-3-urp-stylised-water/
- Jesús Caro. (2020). ¿Cómo crear un shader toon con un modelo de luz custom y Shader Graph?. 25/05/2021, de Dev Sitio web: https://dev.to/jfcarocota/como-crear-un-shader-toon-con-un-modelo-de-luz-custom-y-shader-graph-1c09
- Kalupahana, D. (2019, 20 junio). Shaders in Unity — Lambert and Ambient - Deshan Kalupahana. Medium. Recuperado de: https://medium.com/@deshankalupahana/shaders-in-unity-lambert-and-ambient-ceba9fab6cfa
- Lindman, A. (2019, 31 julio). Custom Lighting in Shader Graph: Expanding your graphs in 2019. Unity Blog. Recuperado de: https://blog.unity.com/technology/custom-lighting-in-shader-graph-expanding-your-graphs-in-2019
- Miciuleviciute, P. (2021). Paulinami. Water Shader [URP, Amplify]. Recuperado de: https://www.paulinami.com/water-shader-urp-amplify
- P. (s. f.). 5.1. Definición, características y objetivo del método experimental. Psikipedia. Recuperado de: https://psikipedia.com/libro/analisis-de-datos/2458-la-distribucion-t-de-student#:%7E:text=Una%20distribuci%C3%B3n%20%E2%80%9Ct%E2%80%9D%20es%20el,sim%C3%A9trica%2C%20con%20%CE%BC%20%3D%200.
- P. (s. f.). 5.1. Definición, características y objetivo del método experimental. Psikipedia. Recuperado de: https://psikipedia.com/libro/analisis-de-datos/2458-la-distribucion-t-de-student#:%7E:text=Una%20distribuci%C3%B3n%20%E2%80%9Ct%E2%80%9D%20es%20el,sim%C3%A9trica%2C%20con%20%CE%BC%20%3D%200.
- School, A. C. T. D. (2019, 12 junio). Cel Shading ó Toon Shading. THE CUBE. https://www.thecube3danimation.com/blog-1/2018/1/29/cel-shading-toon-shading
- Shader Graph Low Poly Water. (2021, 6 marzo). Game Developers Hub. https://game-developers.org/shader-graph-low-poly-water/
- Strix, S. (2016). Stix Games. DirectX 11 Grass Shader. Recuperado de: https://stixgames.com/publicfiles/StixGames%20-%20DirectX%2011%20Grass%20Shader%20Manual.pdf
- Technologies, U. (2021). Unity. Shader Graph: Tiling and Offset. Recuperado de: https://learn.unity.com/tutorial/shader-graph-tiling-and-offset-2019-3#
- Technologies, U. (2021). Unity. Subtract Node. Recuperado de: https://docs.unity.cn/Packages/com.unity.shadergraph@6.9/manual/Subtract-Node.html
- Technologies, U. (2021). Unity. Subtract Node. Recuperado de: https://docs.unity.cn/Packages/com.unity.shadergraph@6.9/manual/Subtract-Node.html
- Tuttle, J. (2019, 1 noviembre). Unity Water Shaders - Jason Tuttle. Medium. https://medium.com/@JasonTuttle/unity-water-shaders-2b615e696adc
- Tuttle, J. (2019, 1 noviembre). Unity Water Shaders - Jason Tuttle. Medium. https://medium.com/@JasonTuttle/unity-water-shaders-2b615e696adc
- Unity Technologies. (2018). Agua en Unity. 25/05/2021, de Unity Sitio web: https://docs.unity3d.com/es/2018.4/Manual/HOWTO-Water.html
- Unity Toon Shader Tutorial at Roystan. (s. f.). Roystan. Recuperado 21 de mayo de 2021, de https://roystan.net/articles/toon-shader.html
- Vertex Displacement. (2018, 16 junio). Ronja&#39;s Tutorials. https://www.ronja-tutorials.com/post/015-wobble-displacement/
- Vertex Displacement. (2018, 16 junio). Ronja&#39;s Tutorials. https://www.ronja-tutorials.com/post/015-wobble-displacement/
- Vertex Shader - OpenGL Wiki. (2017, November 10). OpenGL Wiki. https://www.khronos.org/opengl/wiki/Vertex\_Shader
- Vertex Shader - OpenGL Wiki. (2017, November 10). OpenGL Wiki. https://www.khronos.org/opengl/wiki/Vertex\_Shader
- Zucconi, A. (2020, 29 julio). Vertex and fragment shaders in Unity3D. Alan Zucconi. https://www.alanzucconi.com/2015/07/01/vertex-and-fragment-shaders-in-unity3d/
