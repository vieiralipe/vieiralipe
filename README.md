from manim import *

class IntegralDeRiemann(Scene):
  
    def construct(self):
        txt1 = Title('Somas de Riemann')
        txt2 = Title('Somas de Riemann - Visualização')
        
        self.play(FadeIn(txt1))
        self.wait(0.5)
        self.play(Transform(txt1,txt2))
        self.wait()

        txt3 = Text('A seguir, teremos 4 exemplos de integral definida entre 0 e 3,').scale(0.6)
        txt4 = Text('neles, podemos observar o conceito por trás do').scale(0.6).next_to(txt3,DOWN)
        txt5 = Text('Somatório de Riemann').scale(0.6).next_to(txt4,DOWN)
        txt6 = MathTex(r"A(a, b, f) = \int_{a}^{b} f(x) dx = \lim_{n \to \infty} \sum _{i=1} ^{n} f{\left( {a+i\frac{b-a}{n}} \right)} \frac{b-a}{n}")

        self.play(FadeIn(txt3,txt4,txt5))
        self.wait(6.5)
        self.play(FadeOut(txt3,txt4,txt5))
        self.wait(0.25)
        self.play(FadeIn(txt6))
        self.wait(10)
        self.play(FadeOut(txt6))
        self.wait(0.25)

        t1 = MathTex("Exemplo ~ 1: {x}+{1}").scale(0.9).next_to(txt1,DOWN)

        self.play(FadeIn(t1))

        ax = Axes(
            x_range=[-2, 8, 1],
            y_range=[0, 8, 1],
            tips=False,
            axis_config={"include_numbers": True}
        ).scale(0.8).next_to(txt1, DOWN, buff=1.2)
        graph1 = ax.plot(lambda x: x + 1, x_range=[-2, 7], use_smoothing=False)
        self.play(Create(ax))
        self.wait()
        self.play(Create(graph1))
        self.wait()
        
        rects = VGroup()

        rects_right10 = ax.get_riemann_rectangles(
            graph1,
            x_range=[0, 3],
            dx=0.2,
            color=(YELLOW_A, MAROON_A, BLUE_A, GREEN_A),
            input_sample_type="right",
        )
        rects_right11 = ax.get_riemann_rectangles(
            graph1,
            x_range=[0, 3],
            dx=0.1,
            color=(YELLOW_A, MAROON_A, BLUE_A, GREEN_A),
            input_sample_type="right",
        )
        rects_right12 = ax.get_riemann_rectangles(
            graph1,
            x_range=[0, 3],
            dx=0.025,
            color=(YELLOW_A, MAROON_A, BLUE_A, GREEN_A),
            input_sample_type="right",
        )

        self.play(Create(rects_right10))
        self.wait(1.5)
        self.play(Uncreate(rects_right10))
        self.play(Create(rects_right11))
        self.wait(1.5)
        self.play(Uncreate(rects_right11))
        self.play(Create(rects_right12))
        self.wait(1.5)
        self.play(Uncreate(rects_right12))

        t2 = MathTex("Exemplo ~ 2: {(x-2)}^{2}+{1}").scale(0.9).next_to(txt1,DOWN)

        self.play(Transform(t1,t2))

        graph2 = ax.plot(lambda x: (x-2) ** 2 + 1, x_range=[-0.65, 4.65], use_smoothing=False)
        self.play(Uncreate(graph1))
        self.play(Create(graph2))
        
        rects = VGroup()

        rects_right20 = ax.get_riemann_rectangles(
            graph2,
            x_range=[0, 3],
            dx=0.2,
            color=(YELLOW_A, MAROON_A, BLUE_A, GREEN_A),
            input_sample_type="right",
        )
        rects_right21 = ax.get_riemann_rectangles(
            graph2,
            x_range=[0, 3],
            dx=0.1,
            color=(YELLOW_A, MAROON_A, BLUE_A, GREEN_A),
            input_sample_type="right",
        )
        rects_right22 = ax.get_riemann_rectangles(
            graph2,
            x_range=[0, 3],
            dx=0.025,
            color=(YELLOW_A, MAROON_A, BLUE_A, GREEN_A),
            input_sample_type="right",
        )

        self.play(Create(rects_right20))
        self.wait(1.5)
        self.play(Uncreate(rects_right20))
        self.play(Create(rects_right21))
        self.wait(1.5)
        self.play(Uncreate(rects_right21))
        self.play(Create(rects_right22))
        self.wait(1.5)
        self.play(Uncreate(rects_right22))
 
        t3 = MathTex(r"Exemplo ~ 3: -\frac{1}{2}(x-3)^{3}+{3(x-3)}+{3}").scale(0.9).next_to(txt1,DOWN)

        self.play(Transform(t1,t3))

        graph3 = ax.plot(lambda x: (-1)*(1/2)*(x-3) ** 3 + 3*(x-3) + 3, x_range=[-0.05, 8], use_smoothing=False)
        self.play(Uncreate(graph2))
        self.play(Create(graph3))
        
        rects = VGroup()

        rects_right30 = ax.get_riemann_rectangles(
            graph3,
            x_range=[0, 3],
            dx=0.2,
            color=(YELLOW_A, MAROON_A, BLUE_A, GREEN_A),
            input_sample_type="right",
        )
        rects_right31 = ax.get_riemann_rectangles(
            graph3,
            x_range=[0, 3],
            dx=0.1,
            color=(YELLOW_A, MAROON_A, BLUE_A, GREEN_A),
            input_sample_type="right",
        )
        rects_right32 = ax.get_riemann_rectangles(
            graph3,
            x_range=[0, 3],
            dx=0.025,
            color=(YELLOW_A, MAROON_A, BLUE_A, GREEN_A),
            input_sample_type="right",
        )

        self.play(Create(rects_right30))
        self.wait(1.5)
        self.play(Uncreate(rects_right30))
        self.play(Create(rects_right31))
        self.wait(1.5)
        self.play(Uncreate(rects_right31))
        self.play(Create(rects_right32))
        self.wait(1.5)
        self.play(Uncreate(rects_right32))

        t4 = MathTex(r" Exemplo ~ 4: sen(x) + 1").scale(0.9).next_to(txt1,DOWN)

        self.play(Transform(t1,t4))

        graph4 = ax.plot(lambda x: np.sin(x) + 1, x_range=[-2, 8], use_smoothing=False)
        self.play(Uncreate(graph3))
        self.play(Create(graph4))
        
        rects = VGroup()

        rects_right40 = ax.get_riemann_rectangles(
            graph4,
            x_range=[0, 3],
            dx=0.2,
            color=(YELLOW_A, MAROON_A, BLUE_A, GREEN_A),
            input_sample_type="right",
        )
        rects_right41 = ax.get_riemann_rectangles(
            graph4,
            x_range=[0, 3],
            dx=0.1,
            color=(YELLOW_A, MAROON_A, BLUE_A, GREEN_A),
            input_sample_type="right",
        )
        rects_right42 = ax.get_riemann_rectangles(
            graph4,
            x_range=[0, 3],
            dx=0.025,
            color=(YELLOW_A, MAROON_A, BLUE_A, GREEN_A),
            input_sample_type="right",
        )

        self.play(Create(rects_right40))
        self.wait(1.5)
        self.play(Uncreate(rects_right40))
        self.play(Create(rects_right41))
        self.wait(1.5)
        self.play(Uncreate(rects_right41))
        self.play(Create(rects_right42))
        self.wait(1.5)
        self.play(Uncreate(rects_right42))
        self.wait()
        self.play(FadeOut(graph4,ax,t1 ))
        self.wait()        
        
        txt6 = Text('Com isso, observamos que, quanto mais retângulos com base' ).scale(0.6)
        txt7 = Text('sendo metade do tamanho anterior desenhamos, mais aproximamos' ).scale(0.6).next_to(txt6,DOWN)
        txt8 = Text('o valor das somas dos retângulos com a A(a, b, f)' ).scale(0.6).next_to(txt7,DOWN)

        self.play(FadeIn(txt6,txt7,txt8))
        self.wait(9)
        self.play(FadeOut(txt6,txt7,txt8))



class Abc(Scene):
  
    def construct(self):
        txt1 = Title('Somas de Riemann')
        txt2 = Title('Somas de Riemann - Visualização')
        
        self.play(FadeIn(txt1))
        self.wait(0.5)
        self.play(Transform(txt1,txt2))
        self.wait()
       

        t1 = MathTex(r"Exemplo ~ 3: -\frac{1}{2}(x-3)^{3}+{3(x-3)}+{3}").scale(0.9).next_to(txt1,DOWN)

        self.play(FadeIn(t1))

        ax = Axes(
            x_range=[-2, 8, 1],
            y_range=[0, 8, 1],
            tips=False,
            axis_config={"include_numbers": True}
        ).scale(0.8).next_to(txt1, DOWN, buff=1.2)
        graph1 = ax.plot(lambda x: x + 1, x_range=[-2, 7], use_smoothing=False)
        self.play(Create(ax))
        self.wait()
        self.play(Create(graph1))
        self.wait()
        
        rects = VGroup()

        rects_right10 = ax.get_riemann_rectangles(
            graph1,
            x_range=[0, 3],
            dx=0.2,
            color=(YELLOW_A, MAROON_A, BLUE_A, GREEN_A),
            input_sample_type="right",
        )
        rects_right11 = ax.get_riemann_rectangles(
            graph1,
            x_range=[0, 3],
            dx=0.1,
            color=(YELLOW_A, MAROON_A, BLUE_A, GREEN_A),
            input_sample_type="right",
        )
        rects_right12 = ax.get_riemann_rectangles(
            graph1,
            x_range=[0, 3],
            dx=0.025,
            color=(YELLOW_A, MAROON_A, BLUE_A, GREEN_A),
            input_sample_type="right",
        )

        self.play(Create(rects_right10))
        self.wait(1.5)
        self.play(Uncreate(rects_right10))
        self.play(Create(rects_right11))
        self.wait(1.5)
        self.play(Uncreate(rects_right11))
        self.play(Create(rects_right12))
        self.wait(1.5)
        self.play(Uncreate(rects_right12))
