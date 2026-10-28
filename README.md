<html>
   <meta charset="UTF-8">
  import { type ReactNode } from 'react';
import { QueryClient, QueryClientProvider } from '@tanstack/react-query';
import { ArrowDownRight, ArrowRight, ArrowUpRight, CalendarDays } from 'lucide-react';
import { ErrorBoundary } from '@/components/error-boundary';
import { Toaster } from '@/components/ui/toaster';
import { TooltipProvider } from '@/components/ui/tooltip';
import NotFound from '@/pages/not-found';
import {
  Route,
  Switch,
  useLocation,
  Router as WouterRouter,
} from 'wouter';

const queryClient = new QueryClient();

function Home() {
  return (
    <main className="site-shell">
      <header className="topbar">
        <a className="brand" href="#home" aria-label="Cowell Student Senate home">
          <span className="brand-mark" aria-hidden="true">C</span>
          <span>Cowell Student Senate<small>University of California, Santa Cruz</small></span>
        </a>
        <nav className="nav-links" aria-label="Main navigation">
          <a href="#about">About</a>
          <a href="#participate">Get involved</a>
          <a href="#meetings">Meetings</a>
          <a className="nav-cta" href="#first-step">Find your way in <ArrowUpRight size={14} aria-hidden="true" /></a>
        </nav>
      </header>
    
      <section className="hero" id="home" aria-labelledby="hero-title">
        <div className="hero-inner">
          <div className="hero-copy">
            <div className="eyebrow">A student-run part of Cowell</div>
            <h1 id="hero-title">A seat at<br />the <em>table.</em></h1>
            <p>Cowell Senate is the student governing board of Cowell College. It’s a place for students to take part in the conversations shaping their shared college community.</p>
            <div className="hero-actions">
              <a className="button-primary" href="#participate">See how to participate <ArrowRight size={15} aria-hidden="true" /></a>
              <a className="button-quiet" href="#about">Get to know the Senate <ArrowDownRight size={16} aria-hidden="true" /></a>
            </div>
            <div className="hero-note"><span className="note-dot" aria-hidden="true" /> Every Cowell student is eligible to be a voting member.</div>
          </div>
          <div className="hero-art" role="img" aria-label="Illustration of a campus hillside, sunset, and winding path">
            <div className="orbit" aria-hidden="true" />
            <div className="orbit orbit-two" aria-hidden="true" />
            <div className="sun-disc" aria-hidden="true" />
            <div className="art-card" aria-hidden="true">
              <div className="art-card-top"><span>Santa Cruz, California</span><span>36° 58′ N</span></div>
              <div className="art-illustration"><span className="art-sun" /><span className="art-hill" /><span className="art-hill-two" /><span className="art-path" /></div>
              <div className="art-title"><strong>Here,<br />together.</strong><span>COWELL COLLEGE · UCSC</span></div>
            </div>
            <span className="floating-label label-one">A voice in the room</span>
            <span className="floating-label label-two">Students belong here</span>
          </div>
        </div>
        <span className="vertical-note">THE COWELL COMMUNITY · SINCE 1965</span>
      </section>

      <div className="ticker" aria-label="Student voice, shared community, open invitation">
        <div className="ticker-track">
          <span>Student voice <i /></span><span>Shared community <i /></span>
          <span>Room to take part <i /></span><span>Student voice <i /></span>
        </div>
      </div>

      <section className="section intro-section" id="about">
        <div className="section-inner intro-grid">
          <div className="section-index">01 / What it is</div>
          <div>
            <h2 className="intro-title">A college community is made by the people <em>in it.</em></h2>
            <p className="intro-copy">Cowell Senate is Cowell College’s student governing board. Students bring their perspectives into a shared space and take part in student governance. You don’t need to arrive with a speech prepared or know how everything works. Being curious is a perfectly good place to begin.</p>
          </div>
        </div>
      </section>

      <section className="statement-band" aria-labelledby="statement-title">
        <div className="statement-grid">
          <h2 id="statement-title">Not just for the loudest voice in the room.</h2>
          <div>
            <p>There’s no single way a Cowell student has to sound, think, or show up to belong in a conversation about the college. Your point of view is part of the community, too.</p>
            <div className="small-note">Different perspectives make a fuller picture.</div>
          </div>
        </div>
      </section>

      <section className="section how-section" id="participate">
        <div className="section-inner">
          <div className="section-heading">
            <div><div className="section-index">02 / Getting involved</div><h2>Start small.<br />Show up as you are.</h2></div>
            <p>Participation can begin with listening. The next step is yours to choose.</p>
          </div>
          <div className="step-list">
            <article className="step-row">
              <span className="step-number">01 /</span><h3>Get a feel for it</h3>
              <p>Learn what the Senate is and how it fits into Cowell College. You’re allowed to start with questions.</p>
            </article>
            <article className="step-row">
              <span className="step-number">02 /</span><h3>Come to a meeting</h3>
              <p>Senate meets weekly on Thursday evenings, according to Cowell’s official Student Programs page. Check there for the latest meeting details.</p>
            </article>
            <article className="step-row">
              <span className="step-number">03 /</span><h3>Take part</h3>
              <p>Every Cowell student is eligible to become a full voting member. Find the current participation details through Cowell Student Programs.</p>
            </article>
          </div>
        </div>
      </section>

      <section className="section eligibility" aria-labelledby="eligibility-heading">
        <div className="section-inner eligibility-grid">
          <div>
            <div className="section-index">03 / Who can join</div>
            <h2 id="eligibility-heading">If you’re a Cowell student, <em>you’re eligible.</em></h2>
            <p>Every Cowell student is eligible to become a full voting member of Cowell Senate. You don’t have to wait until you feel like an expert to find out more or take part.</p>
          </div>
          <div className="eligibility-art" aria-hidden="true">
            <span className="orbit-point p1" /><span className="orbit-point p2" /><span className="orbit-point p3" />
            <div className="eligibility-word">Your voice<br />belongs here.</div>
          </div>
        </div>
      </section>

      <section className="section meet-section" id="meetings">
        <div className="section-inner">
          <div className="section-index">04 / Find a time</div>
          <div className="meeting-card">
            <div className="meeting-aside"><span>Make room for the conversation</span><strong>Bring your<br />curiosity.</strong></div>
            <div className="meeting-main">
              <h2>See you Thursday?</h2>
              <p>The official Cowell Student Programs page currently lists Senate meetings as weekly on Thursday evenings. For the latest time, location, and participation details, use the official page before you go.</p>
              <div className="meeting-meta"><CalendarDays aria-hidden="true" /> Weekly · Thursday evenings</div>
            </div>
          </div>
        </div>
      </section>

      <section className="section faq-section" id="first-step">
        <div className="section-inner faq-grid">
          <div>
            <div className="section-index">05 / A few things to know</div>
            <h2>Questions are a good first step.</h2>
          </div>
          <div className="faq-list">
            <details className="faq-item">
              <summary>Do I have to be an elected officer to participate?</summary>
              <p>No. Every Cowell student is eligible to become a full voting member. Visit the official Student Programs page for current participation details.</p>
            </details>
            <details className="faq-item">
              <summary>What if I’ve never been to a meeting?</summary>
              <p>Everyone starts somewhere. You can look up the latest meeting details on Cowell’s official page and come ready to listen, learn, or take part.</p>
            </details>
            <details className="faq-item">
              <summary>Where can I find the most up-to-date information?</summary>
              <p>Cowell’s Student Programs page is the official source for current participation and meeting details. Check it before making plans.</p>
            </details>
          </div>
        </div>
      </section>

      <section className="last-call" aria-labelledby="last-call-title">
        <div className="closing-orb" aria-hidden="true" />
        <div className="last-call-inner">
          <div>
            <div className="section-index">Your next step can be simple</div>
            <h2 id="last-call-title">There’s room<br />for <em>your voice.</em></h2>
          </div>
          <a className="button-primary" href="https://cowell.ucsc.edu/student-opportunities/student-programs/" target="_blank" rel="noreferrer" data-testid="link-official-student-programs">
            Visit Cowell Student Programs <ArrowUpRight size={16} aria-hidden="true" />
          </a>
        </div>
      </section>

      <footer className="footer">
        <div className="footer-mark">Cowell Student Senate</div>
        <p>A student-centered introduction to Cowell’s student governing board.</p>
        <a href="https://cowell.ucsc.edu/student-opportunities/student-programs/" target="_blank" rel="noreferrer">Official participation &amp; meeting details <ArrowUpRight size={12} aria-hidden="true" /></a>
      </footer>
    </main>
  );
}

function Router() {
  return (
    // Keep a shared shell (sidebar, navbar) outside the boundary so it
    // survives a page crash.
    <RoutedErrorBoundary>
      <Switch>
        <Route path="/" component={Home} />
        <Route component={NotFound} />
      </Switch>
    </RoutedErrorBoundary>
  );
}

function RoutedErrorBoundary({ children }: { children: ReactNode }) {
  const [location] = useLocation();
  return <ErrorBoundary resetKey={location}>{children}</ErrorBoundary>;
}

function App() {
  return (
    <QueryClientProvider client={queryClient}>
      <TooltipProvider>
        <WouterRouter base={import.meta.env.BASE_URL.replace(/\/$/, '')}>
          <Router />
        </WouterRouter>
        <Toaster />
      </TooltipProvider>
    </QueryClientProvider>
  );
}
  <link rel="stylesheet" href="./css/style.css">
export default App;
</html>
