# AAEproyect
**PROYECTO FINAL**

**TÓPICOS DE FÍSICA**

_ **Equipo:** _

- Aguilar Morales Alma Delfina
- Zamora Gámez Jesús Armando
- Pereo Torres Erik Rodrigo

Tradicionalmente, las personas con cierto conocimiento de programación son quienes se han ocupado de crear los shaders en Unity. Shader Graph da la posibilidad a los artistas y otros integrantes del equipo, gracias a que permite crear shaders muy fácilmente, tal como los que se presentan en el proyecto.

**GLSL**

Un shader es un pequeño programa que se ejecuta directamente en el procesador de la placa de video (GPU). Esto permite hacer efectos gráficos con muy poco impacto en el rendimiento. Las CPUs no están orientadas a gráficos, matemática de vectores, matrices, mientras que las GPUs sí, y además están pensadas para trabajar de forma paralela.

Básicamente hay tres tipos de shaders:

Vertex Shaders: se ejecutan una vez por cada vértice que forma parte del elemento que se quiere renderizar. Permiten hacer efectos sobre los propios vértices, es decir, moverlos para hacer algún efecto de distorsión (aplicar una función trigonométrica como seno podría servir para simular las olas de un océano, por ejemplo). Su valor de retorno es la posición del vértice procesada.

Pixel Shaders (en OpenGL los llaman Fragment Shader): se ejecutan una vez por cada fragmento visible de la imagen (es decir, la cantidad de veces que se ejecuten depende de la vista de cámara, tamaño del objeto y otros factores más). Su valor de retorno es el color del pixel resultante. Con la ayuda de los vertex shaders, permiten hacer efectos vistosos como iluminación, cel shading, bump mapping, y una gran cantidad de filtros de post-procesamiento como desenfoque, profundidad de campo, desenfoque de movimiento, bloom, hdr, entre otros.

Geometry Shaders: se ejecutan por cada cara del modelo que se quiere renderizar. Tienen la particularidad que pueden crear nuevos vértices por lo que son muy útiles para generar efectos como pasto, pelo, sombras proyectadas, reflejos, etc.

**Efecto Agua**

El agua simple en Unity requiere adjuntar un script a un mesh de tipo plano y usar el shader de agua:

- Tiene un mesh para el agua. Esto debería ser un mesh plano, orientado horizontalmente. Las coordenadas UV no se requieren. El GameObject de agua debería usar la Water layer, la cual usted puede configurar en el Inspector.
- Adjunte un script WaterSimple (de Standard Assets/Water/Sources) al objeto.
- Utilice el FX/Water (simple) shader en el material, o ajuste el que es proporcionado con los materiales de agua (Daylight Simple Water o Nighttime Simple Water).

El agua reflectiva/refractiva requiere algunos pases similares para iniciar de ceros:

- Tiene un mesh para el agua. Esto debería ser un mesh plano, orientado horizontalmente. Las coordenadas UV no se requieren. El GameObject de agua debería usar la Water layer, la cual usted puede configurar en el Inspector.
- Adjunte el script Water (de los Pro-Standard Assets/Water/Sources) al objeto (modo de Water rendering se puede configurar en el Inspector: Simple, Reflective o Refractive.)
- Utilice el FX/Water shader en el material, o ajuste uno de los materiales de agua proporcionados (Daylight Water o Nighttime Water).

Las propiedades presentadas a continuación son utilizadas en el Reflective &amp; Refractive water shader. La mayoría de estos son utilizados en un simple water shader también:

- Wave scale: La escala de las ondas del normal map. Entre menos sea el valor, más grandes serán las olas.
- Reflection/refraction distort: Qué tanta reflection (reflejo) /refraction (refracción) es distorsionada por las olas del normal map.
- Refraction color: Tinte adicional para la refracción.
- Environment reflection/refraction: Renderiza texturas para reflejos y refracciones en tiempo real.
- Normalmap: Define la forma de las olas. Las olas finales son producidas al combinar estas dos normal maps, cada desplazamiento en una dirección diferente, escala y velocidad. El segundo normal map es la mitad de grande que el primero.
- Wave speed: La velocidad de desplazamiento para el primer normal map (1ros y 2ndos números) y el segundo normal map (3eros y 4tos números).
- Fresnel: Una textura con el canal alpha controlando el efecto Fresnel - qué tanta reflection (reflejo) vs refraction (refracción) es visible, basado en el ángulo de vista.

El resto de las propiedades no son utilizadas por el Reflective &amp; Refractive shader por si solos, pero necesitan estar en caso de que la tarjeta de video del usuario no lo soporte y debe fallback a un shader más simple:

- Reflective color/cube y fresnel: Una textura que define el color del agua (RGB) y el efecto Fresnel (A) basándose en la vista del ángulo.
- Horizon color: El color del agua en el horizonte. (Utilizado con el simple water shader)
- Fallback textura: Una textura utilizada para representar el agua en tarjetas de video muy viejas, si ninguno de los mejores shaders lo pueden correr.

**Toon Shading**

La ley de Lambert trata sobre la iluminancia de una superficie situada a una cierta distancia de una fuente de luz. Determina que la iluminación producida por una fuente luminosa sobre una superficie es directamente proporcional a la intensidad de la fuente y al coseno del ángulo que forma la normal a la superficie con la dirección de los rayos de luz y es inversamente proporcional al cuadrado de la distancia a dicha fuente.

Toon shading, o cell shading, es una técnica de renderización no fotorrealista que hace que los modelos 3D parezcan planos. Volver a crear la apariencia de un shader toon utilizando solo funciones de superficie sería extremadamente costoso. Además, como el shader toon requiere que cambiemos la forma en que se refleja la luz, es un problema, en su lugar necesitamos un modelo de iluminación personalizado. Algunas implementaciones del shader Toon utilizan una textura llamada mapa de Ramp para definir la forma en que reasignamos la intensidad de luz de Lambert (NdotL) a otro valor.

Abstract

En el presente proyecto se muestra el trabajo final del semestre, siendo este él resultado de los aprendizajes obtenidos a lo largo de las clases de Tópicos de Física. En dicho proyecto se muestran elementos codificados con la finalidad de asimilarse a la realidad, tales como modelos de luz y movimiento.

Introducción

Para este proyecto se creó una escena en Unity donde se presentan los elementos solicitados para dicho trabajo en base a lo aprendido y aplicado en el transcurso del semestre:

-Modelo de agua con vertex shading

-Vegetación con vertex shading

-Modelo de luz custom

 **Video:**
 https://drive.google.com/drive/folders/1BWDHbmXisKzas6CjPvyxorWm3f2zTaxv?usp=sharing

Referencias

1. Anónimo. (s.f.). Superficie de agua simulada con animación de caso-vértice. 25/05/2021, de programador clic Sitio web: [https://programmerclick.com/article/82521837246/](https://programmerclick.com/article/82521837246/)
2. Unity Technologies. (2018). Agua en Unity. 25/05/2021, de Unity Sitio web: [https://docs.unity3d.com/es/2018.4/Manual/HOWTO-Water.html](https://docs.unity3d.com/es/2018.4/Manual/HOWTO-Water.html)
3. Antonio Moon. (2019). Shaders (Ley de Lambert) y Cell Shading (Toon). 25/05/2021, de GitHub Sitio web: [https://moonantonio.github.io/post/2019/dev/002/#:~:text=Cell%20Shader,los%20modelos%203D%20parezcan%20planos.&amp;text=Algunas%20implementaciones%20del%20shader%20Toon,(NdotL)%20a%20otro%20valor](https://moonantonio.github.io/post/2019/dev/002/#:~:text=Cell%20Shader,los%20modelos%203D%20parezcan%20planos.&amp;text=Algunas%20implementaciones%20del%20shader%20Toon,(NdotL)%20a%20otro%20valor).
4. Vertex Shader - OpenGL Wiki. (2017, November 10). OpenGL Wiki. [https://www.khronos.org/opengl/wiki/Vertex\_Shader](https://www.khronos.org/opengl/wiki/Vertex_Shader)
5. Jesús Caro. (2020). ¿Cómo crear un shader toon con un modelo de luz custom y Shader Graph?. 25/05/2021, de Dev Sitio web: [https://dev.to/jfcarocota/como-crear-un-shader-toon-con-un-modelo-de-luz-custom-y-shader-graph-1c09](https://dev.to/jfcarocota/como-crear-un-shader-toon-con-un-modelo-de-luz-custom-y-shader-graph-1c09)
6. Technologies, U. (2021). Unity. Shader Graph: Tiling and Offset. Recuperado de: [https://learn.unity.com/tutorial/shader-graph-tiling-and-offset-2019-3#](https://learn.unity.com/tutorial/shader-graph-tiling-and-offset-2019-3)
7. Technologies, U. (2021). Unity. Subtract Node. Recuperado de: [https://docs.unity.cn/Packages/com.unity.shadergraph@6.9/manual/Subtract-Node.html](https://docs.unity.cn/Packages/com.unity.shadergraph@6.9/manual/Subtract-Node.html)
8. Vertex Displacement. (2018, 16 junio). Ronja&#39;s Tutorials. [https://www.ronja-tutorials.com/post/015-wobble-displacement/](https://www.ronja-tutorials.com/post/015-wobble-displacement/)
9. School, A. C. T. D. (2019, 12 junio). Cel Shading ó Toon Shading. THE CUBE. [https://www.thecube3danimation.com/blog-1/2018/1/29/cel-shading-toon-shading](https://www.thecube3danimation.com/blog-1/2018/1/29/cel-shading-toon-shading)
10. Strix, S. (2016). Stix Games. DirectX 11 Grass Shader. Recuperado de: [https://stixgames.com/publicfiles/StixGames%20-%20DirectX%2011%20Grass%20Shader%20Manual.pdf](https://stixgames.com/publicfiles/StixGames%20-%20DirectX%2011%20Grass%20Shader%20Manual.pdf)
11. Tuttle, J. (2019, 1 noviembre). Unity Water Shaders - Jason Tuttle. Medium. [https://medium.com/@JasonTuttle/unity-water-shaders-2b615e696adc](https://medium.com/@JasonTuttle/unity-water-shaders-2b615e696adc)
12. Kalupahana, D. (2019, 20 junio). Shaders in Unity — Lambert and Ambient - Deshan Kalupahana. Medium. Recuperado de: [https://medium.com/@deshankalupahana/shaders-in-unity-lambert-and-ambient-ceba9fab6cfa](https://medium.com/@deshankalupahana/shaders-in-unity-lambert-and-ambient-ceba9fab6cfa)
13. Lindman, A. (2019, 31 julio). Custom Lighting in Shader Graph: Expanding your graphs in 2019. Unity Blog. Recuperado de: [https://blog.unity.com/technology/custom-lighting-in-shader-graph-expanding-your-graphs-in-2019](https://blog.unity.com/technology/custom-lighting-in-shader-graph-expanding-your-graphs-in-2019)
14. Creating water with shader graph in unity| 2D shader basics. (2020, 27 octubre). CGTubes. [https://www.cgtutes.com/water-shader-graph-unity/](https://www.cgtutes.com/water-shader-graph-unity/)
15. Tuttle, J. (2019, 1 noviembre). Unity Water Shaders - Jason Tuttle. Medium. [https://medium.com/@JasonTuttle/unity-water-shaders-2b615e696adc](https://medium.com/@JasonTuttle/unity-water-shaders-2b615e696adc)
16. Anónimo. (2021). Game Dev. Water Shader. Recuperado de: [https://gamedev.stackexchange.com/questions/183143/need-to-generate-seamless-gradient-noise-texture-for-water-shader?noredirect=1&amp;lq=1](https://gamedev.stackexchange.com/questions/183143/need-to-generate-seamless-gradient-noise-texture-for-water-shader?noredirect=1&amp;lq=1)
17. Vertex Displacement. (2018, 16 junio). Ronja&#39;s Tutorials. [https://www.ronja-tutorials.com/post/015-wobble-displacement/](https://www.ronja-tutorials.com/post/015-wobble-displacement/)
18. Anónimo. (2018). RoyStan. Grass Shader. Recuperado de: [https://roystan.net/articles/grass-shader.html](https://roystan.net/articles/grass-shader.html)
19. Vertex Shader - OpenGL Wiki. (2017, November 10). OpenGL Wiki. [https://www.khronos.org/opengl/wiki/Vertex\_Shader](https://www.khronos.org/opengl/wiki/Vertex_Shader)
20. Technologies, U. (2021). Unity. Subtract Node. Recuperado de: [https://docs.unity.cn/Packages/com.unity.shadergraph@6.9/manual/Subtract-Node.html](https://docs.unity.cn/Packages/com.unity.shadergraph@6.9/manual/Subtract-Node.html)
21. Shader Graph Low Poly Water. (2021, 6 marzo). Game Developers Hub. [https://game-developers.org/shader-graph-low-poly-water/](https://game-developers.org/shader-graph-low-poly-water/)
22. Creating water with shader graph in unity| 2D shader basics. (2020, 27 octubre). CGTubes. [https://www.cgtutes.com/water-shader-graph-unity/](https://www.cgtutes.com/water-shader-graph-unity/)
23. Unity Toon Shader Tutorial at Roystan. (s. f.). Roystan. Recuperado 21 de mayo de 2021, de [https://roystan.net/articles/toon-shader.html](https://roystan.net/articles/toon-shader.html)
24. Ilett, D. (2020, 5 abril). Stylised Water in Shader Graph and URP. Daniel Ilett: Games | Shaders | Tutorials. [https://danielilett.com/2020-04-05-tut5-3-urp-stylised-water/](https://danielilett.com/2020-04-05-tut5-3-urp-stylised-water/)
25. Creating water with shader graph in unity| 2D shader basics. (2020, 27 octubre). CGTubes. [https://www.cgtutes.com/water-shader-graph-unity/](https://www.cgtutes.com/water-shader-graph-unity/)
26. Miciuleviciute, P. (2021). Paulinami. Water Shader [URP, Amplify]. Recuperado de: [https://www.paulinami.com/water-shader-urp-amplify](https://www.paulinami.com/water-shader-urp-amplify)
27. P. (s. f.). 5.1. Definición, características y objetivo del método experimental. Psikipedia. Recuperado de: [https://psikipedia.com/libro/analisis-de-datos/2458-la-distribucion-t-de-student#:%7E:text=Una%20distribuci%C3%B3n%20%E2%80%9Ct%E2%80%9D%20es%20el,sim%C3%A9trica%2C%20con%20%CE%BC%20%3D%200](https://psikipedia.com/libro/analisis-de-datos/2458-la-distribucion-t-de-student#:%7E:text=Una%20distribuci%C3%B3n%20%E2%80%9Ct%E2%80%9D%20es%20el,sim%C3%A9trica%2C%20con%20%CE%BC%20%3D%200).
28. Anónimo. (2018). RoyStan. Toon Shader. Recuperado de: [https://roystan.net/articles/toon-shader.html](https://roystan.net/articles/toon-shader.html)
29. P. (s. f.). 5.1. Definición, características y objetivo del método experimental. Psikipedia. Recuperado de: [https://psikipedia.com/libro/analisis-de-datos/2458-la-distribucion-t-de-student#:%7E:text=Una%20distribuci%C3%B3n%20%E2%80%9Ct%E2%80%9D%20es%20el,sim%C3%A9trica%2C%20con%20%CE%BC%20%3D%200](https://psikipedia.com/libro/analisis-de-datos/2458-la-distribucion-t-de-student#:%7E:text=Una%20distribuci%C3%B3n%20%E2%80%9Ct%E2%80%9D%20es%20el,sim%C3%A9trica%2C%20con%20%CE%BC%20%3D%200).
30. Zucconi, A. (2020, 29 julio). Vertex and fragment shaders in Unity3D. Alan Zucconi. [https://www.alanzucconi.com/2015/07/01/vertex-and-fragment-shaders-in-unity3d/](https://www.alanzucconi.com/2015/07/01/vertex-and-fragment-shaders-in-unity3d/)
