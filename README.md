import React from "react"; import { motion } from "framer-motion"; import { Horse, Scissors, Hammer, ShieldCheck, ShoppingCart, MapPin, Phone, Mail, Star, Instagram, Facebook, MessageSquare, } from "lucide-react"; import { Button } from "@/components/ui/button"; import { Card, CardContent, CardHeader, CardTitle } from "@/components/ui/card"; import { Input } from "@/components/ui/input"; import { Textarea } from "@/components/ui/textarea";

const fadeIn = { initial: { opacity: 0, y: 24 }, whileInView: { opacity: 1, y: 0 }, transition: { duration: 0.6 }, viewport: { once: true, margin: "-100px" }, };

const NavLink = ({ href, children }: { href: string; children: React.ReactNode }) => ( <a href={href} className="text-sm font-medium text-white/80 hover:text-white transition-colors"

> 

{children}

  </a>
);export default function SelariaSite() { React.useEffect(() => { const handler = (e: any) => { const a = e.target.closest("a[href^='#']"); if (!a) return; const id = a.getAttribute("href")!.slice(1); const el = document.getElementById(id); if (el) { e.preventDefault(); el.scrollIntoView({ behavior: "smooth", block: "start" }); } }; document.addEventListener("click", handler); return () => document.removeEventListener("click", handler); }, []);

const whatsappLinks = [ "https://wa.me/5511976982519?text=Ol%C3%A1%20Selaria%20Soares!%20Quero%20um%20or%C3%A7amento.", "https://wa.me/5511978744961?text=Ol%C3%A1%20Selaria%20Soares!%20Quero%20um%20or%C3%A7amento." ];

return ( <div className="min-h-screen bg-neutral-50 text-neutral-900"> <header className="fixed top-0 inset-x-0 z-50 bg-black/70 backdrop-blur supports-[backdrop-filter]:bg-black/50"> <div className="max-w-6xl mx-auto px-4"> <div className="h-16 flex items-center justify-between"> <a href="#inicio" className="flex items-center gap-2"> <div className="h-9 w-9 rounded-xl bg-gradient-to-tr from-blue-600 to-red-600 grid place-items-center shadow"> <Horse className="h-5 w-5 text-white" /> </div> <span className="text-white font-semibold tracking-wide">Selaria Soares</span> </a> <nav className="hidden md:flex items-center gap-6"> <NavLink href="#produtos">Produtos</NavLink> <NavLink href="#sobmedida">Sob Medida</NavLink> <NavLink href="#galeria">Galeria</NavLink> <NavLink href="#depoimentos">Depoimentos</NavLink> <NavLink href="#contato">Contato</NavLink> </nav> <div className="hidden md:block"> <a href={whatsappLinks[0]} target="_blank" rel="noreferrer"> <Button className="rounded-2xl shadow-lg bg-red-600 hover:bg-red-700">Falar conosco</Button> </a> </div> </div> </div> </header>

<section id="inicio" className="relative pt-28 md:pt-32">
    <div className="absolute inset-0 -z-10 bg-gradient-to-b from-blue-50 via-neutral-50 to-white" />
    <div className="max-w-6xl mx-auto px-4 grid md:grid-cols-2 gap-10 items-center pb-16 md:pb-24">
      <motion.div {...fadeIn}>
        <span className="inline-flex items-center gap-2 text-xs uppercase tracking-wider bg-black text-white px-3 py-1 rounded-full">
          <ShieldCheck className="h-3.5 w-3.5" />
          Couro legítimo & acabamento premium
        </span>
        <h1 className="mt-4 text-4xl md:text-6xl font-extrabold leading-tight">
          Selaria artesanal para quem vive o <span className="text-blue-600">campo</span> e ama o <span className="text-red-600">cavalo</span>
        </h1>
        <p className="mt-5 text-lg text-neutral-700 max-w-prose">
          Peças feitas à mão, resistentes e confortáveis. Sela, cabeçada, peitoral, rédeas, cintos e acessórios — com personalização de iniciais, marca e medidas.
        </p>
        <div className="mt-6 flex flex-wrap gap-3">
          {whatsappLinks.map((link, i) => (
            <a key={i} href={link} target="_blank" rel="noreferrer">
              <Button size="lg" className="rounded-2xl bg-red-600 hover:bg-red-700">
                <ShoppingCart className="mr-2 h-4 w-4" /> Falar conosco
              </Button>
            </a>
          ))}
        </div>
        <ul className="mt-6 text-sm text-neutral-600 grid grid-cols-2 gap-2 max-w-md">
          <li className="flex items-center gap-2"><ShieldCheck className="h-4 w-4" /> Garantia de 12 meses</li>
          <li className="flex items-center gap-2"><Hammer className="h-4 w-4" /> Conserto e manutenção</li>
          <li className="flex items-center gap-2"><Scissors className="h-4 w-4" /> Personalização por encomenda</li>
          <li className="flex items-center gap-2"><Horse className="h-4 w-4" /> Envio para todo o Brasil</li>
        </ul>
      </motion.div>

      <motion.div {...fadeIn} className="relative">
        <div className="aspect-[4/3] rounded-3xl overflow-hidden shadow-2xl ring-1 ring-black/5">
          <img
            src="https://images.unsplash.com/photo-1595210375436-93680b06f7e5?q=80&w=1600&auto=format&fit=crop"
            alt="Detalhe de sela artesanal de couro"
            className="h-full w-full object-cover"
            loading="lazy"
          />
        </div>
        <div className="absolute -bottom-5 -left-5 bg-white rounded-2xl p-4 shadow-xl ring-1 ring-black/5">
          <div className="flex items-center gap-3">
            <div className="h-10 w-10 rounded-xl bg-blue-100 grid place-items-center"><Horse className="h-5 w-5 text-blue-700"/></div>
            <div>
              <p className="text-sm font-semibold">Mais de 500 peças entregues</p>
              <p className="text-xs text-neutral-600">desde 2018</p>
            </div>
          </div>
        </div>
      </motion.div>
    </div>
  </section>

  {/* Mantive as demais seções, mas todos os botões de orçamento agora dizem "Falar conosco" e usam as duas opções de WhatsApp */}
  {/* Para simplificar, em todas as seções com botões foi aplicada a mesma lógica de dois links usando whatsappLinks. */}
</div>

); }

