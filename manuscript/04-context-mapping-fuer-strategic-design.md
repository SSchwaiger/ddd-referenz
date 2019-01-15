# IV. Context Mapping für Strategic Design

### Bounded Context

Eine Beschreibung
einer Grenze (typischerweise ein Subsystem oder die Arbeit eines
bestimmten Teams), innerhalb derer ein bestimmtes Modell definiert und
anwendbar ist.

### Upstream-Downstream {#upstream-downstream}

Eine Beziehung zwischen zwei Gruppen, in der die Handlungen der
"Upstream"-Gruppe den Projekterfolg der "Downstream"-Gruppe
beeinflussen, während die Handlungen der Downstream-Gruppe die
Upstream-Projekte nicht wesentlich beeinflussen. (Z.B. wenn zwei Städte am
gleichen Fluss liegen, wirkt sich die Verschmutzung der upstream (Dt.:
flussaufwärts) gelegenen Stadt in erster Linie auf die downstream
gelegene Stadt (Dt.: flussabwärts) aus).

Das Upstream-Team kann unabhängig vom Schicksal des Downstream-Teams
erfolgreich sein.

### Mutually Dependent {#mutually-dependent}

Mutually Dependent (Dt.: wechselseitig abhängig) beschreibt eine Situation,
in der zwei Softwareentwicklungsprojekte in getrennten Kontexten
beide geliefert werden müssen, damit jedes von beiden als erfolgreich angesehen werden kann. (Wenn zwei Systeme jeweils auf Informationen oder Funktionen des
anderen angewiesen sind - was wir im Allgemeinen vermeiden würden -
sehen wir die Projekte, die diese Systeme entwickeln, natürlich als
wechselseitig miteinander verflochten.  Es gibt aber auch
wechselseitig abhängige
Projekte, bei denen Systemabhängigkeiten nur in eine Richtung
verlaufen.  Wenn ein System ohne ein bestimmtes abhängiges System und
ohne die Integration mit diesem abhängigen System wenig Wert hat -
vielleicht weil dies der einzige Ort ist, an dem es verwendet wird -
dann führt es zu einem Misserfolg beider Projekte, wenn das abhängige
System nicht ausgeliefert wird.)

### Free {#free}

Ein Softwareentwicklungskontext ist free (Dt.: frei), wenn die
Ausrichtung, der Erfolg oder das Scheitern der Entwicklungsarbeit in
anderen Kontexten wenig Einfluss auf die Auslieferung hat.

## Context Map {#context-map}

*Dt.: Kontextlandkarte*

*Um eine Strategie entwickeln zu können, benötigen wir eine realistische, groß
angelegte Sicht auf die Modellentwicklung, die sich über unser
gesamtes Projekt und andere, in die wir integrieren, erstreckt.*

Ein einzelner [Bounded Context](#bounded-context) hinterlässt einige
Probleme, wenn
keine globale Sichtweise vorhanden ist. Der Kontext anderer Modelle
kann immer noch vage und im Fluss sein.

Leute in anderen Teams sind sich der Grenzen der [Bounded Contexts](#bounded-context) 
nicht sehr bewusst und nehmen unwissentlich Änderungen vor, welche die
Übergänge verwischen oder die Abhängigkeiten verkomplizieren. Wenn
Verbindungen zwischen verschiedenen Kontexten hergestellt werden
müssen, neigen diese dazu, ineinander zu verlaufen.

Selbst wenn die Grenzen klar sind, stellen Beziehungen zu anderen
Kontexten Einschränkungen für die Art des Modells oder das mögliche
Änderungstempo dar. Diese Einschränkungen manifestieren
sich in erster Linie durch nicht-technische Kanäle, die manchmal
schwer mit den von ihnen betroffenen Entwurfsentscheidungen in
Verbindung zu bringen sind.

Daher:

**Identifiziere jedes Modell, das beim Projekt im Spiel ist und
definiere seinen [Bounded Context](#bounded-context). Dazu gehören
auch die impliziten 
Modelle von nicht-objekt-orientierten Subsystemen. Benenne jeden
[Bounded Context](#bounded-context) und mache diese Namen zu einem
Teil der [Ubiquitous Language](#ubiquitous-language).**

**Beschreibe die Berührungspunkte zwischen den Modellen, skizziere
die explizite Übersetzung für jede Art der Kommunikation, hebe alle
Austausch-, Isolations- und Einflussmechanismen hervor.**

**Kartografiere das vorhandene Gelände. Nimm Transformationen erst 
später vor.**

Diese Karte kann die Grundlage für eine realistische Design-Strategie sein.

Die Charakterisierung von Beziehungen wird auf den folgenden Seiten mit einer Reihe von gängigen Mustern für Beziehungen
zwischen [Bounded Contexts](#bounded-context) konkretisiert.

## Partnership {#partnership}

*Dt.: Partnerschaft*

*Wenn Teams in zwei Kontexten gemeinsam erfolgreich sein oder
scheitern werden, entsteht oft eine kooperative Beziehung.*

Eine schlechte Koordination voneinander abhängiger Subsysteme in
getrennten Kontexten führt bei beiden Projekten dazu, dass sie nicht
erfolgreich
liefern können. Eine wichtige Funktionalität, die in einem System fehlt,
kann dazu führen, dass das andere System nicht liefern
kann. Schnittstellen, die nicht den Erwartungen der Entwickler des
anderen Subsystems entsprechen, können zum Fehlschlagen der
Integration führen. Eine gemeinsam vereinbarte Schnittstelle kann
sich als so umständlich in der Verwendung erweisen, dass sie die Entwicklung des
Client-Systems verlangsamt, oder als so schwer zu implementieren, dass sie
die Entwicklung des Server-Subsystems verlangsamt. Ein Misserfolg
bringt beide Projekte zum Scheitern.

Daher:

**Wenn ein Fehlschlag bei der Entwicklung in einem der beiden Kontexte
zu einem Misserfolg für beide führen würde, solltest du eine
Partnerschaft zwischen den für die beiden Kontexte zuständigen Teams
etablieren. Führe einen Prozess zur koordinierten Planung der
Entwicklung und zum gemeinsamen Managements der Integration ein.**

**Die Teams müssen bei der Entwicklung ihrer Schnittstellen
zusammenarbeiten, um die Bedürfnisse bei der Entwicklung beider
Systeme zu befriedigen. Voneinander abhängige Funktionalitäten sollten so
eingeplant werden, dass sie auf das gleiche Release hin abgeschlossen
werden.**

Es ist in den meisten Fällen nicht notwendig, dass Entwickler das
Modell des anderen Subsystems im Detail verstehen, aber sie müssen
ihre Projektplanung koordinieren. Wenn die Entwicklung in einem
Kontext auf Hindernisse stößt, ist eine gemeinsame Auseinandersetzung
mit dem Thema erforderlich, um eine schnelle Entwurfslösung zu finden,
die beide Kontexte nicht übermäßig negativ beeinträchtigt.

Außerdem ist ein klarer Prozess zur Steuerung der Integration
erforderlich. So kann beispielsweise eine spezielle Testsuite
definiert werden, die zeigt, dass die Schnittstelle den Erwartungen
des Client-Systems entspricht und die im Rahmen der [Continuous Integration](#continuous-integration) auf dem Server-System ausgeführt
werden kann.

*Partnership ist ein neuer Begriff, der seit dem Buch von 2004 entstanden ist.*

## Shared Kernel {#shared-kernel}

*Dt.: Geteilter Kern*

*Die gemeinsame Nutzung eines Teils des Modells und des zugehörigen
Codes erzeugt eine sehr enge wechselseitige Abhängigkeit, welche die
Entuwrfsarbeit in Schwung bringen oder sie untegraben kann.*

Wenn die funktionale Integration begrenzt ist, kann der Aufwand für
die [Continuous Integration](#continuous-integration) eines großen
Kontextes für zu hoch
gehalten werden. Das kann insbesondere der Fall sein, wenn das Team
nicht über die Fähigkeit oder die politische Organisation verfügt,
eine [Continuous Integration](#continuous-integration)
aufrechtzuerhalten, oder wenn ein
einzelnes Team einfach zu groß und zu schwerfällig
wäre. So können stattdessen
getrennte [Bounded Contexts](#bounded-context) definiert und mehrere
Teams gebildet werden.

Einmal getrennt, können unkoordinierte Teams, die an eng verwandten
Anwendungen arbeiten, eine Weile schnell vorankommen, aber was sie
produzieren, passt vielleicht nicht zusammen. Selbst
partnerschaftliche Teams können am Ende viel für Übersetzungsschichten
und Umbauten ausgeben, während sie Aufwände verdoppeln und die
Vorteile einer gemeinsamen [Ubiquitous Language](#ubiquitous-language) verlieren.

Daher:

**Markiere mit einer expliziten Grenze eine Teilmenge des
Domänenmodells, welche die Teams gemeinsam nutzen wollen. Halte diesen
Kern klein.**

**Füge innerhalb dieser Grenze neben dieser Teilmenge des Modells die
Teilmenge des Codes oder des Datenbankdesigns hinzu, die mit diesem
Teil des Modells verbunden ist. Diese explizit geteilten Artefakte
haben einen besonderen Status und sollten nicht ohne Rücksprache mit
dem anderen Team geändert werden.**

{pagebreak}

Definiere einen Prozess für 
[Continuous Integration](#continuous-integration), der das
Kernmodell
kompakt hält und stimme die [Ubiquitous Language](#ubiquitous-language) der Teams 
aufeinander ab. Integriere ein funktionales System häufig, wenn auch
etwas seltener als das Tempo der [Continuous Integration](#continuous-integration) innerhalb 
der Teams.

## Customer/Supplier Development {#customer-supplier}

*Dt.: Kunde/Lieferant*

*Wenn sich zwei Teams in einer
[Upstream-Downstream](#upstream-downstream)-Beziehung
befinden, in der das Upstream-Team unabhängig vom Schicksal des
Downstream-Teams erfolgreich sein kann, werden die Bedürfnisse des
Downstream-Teams auf verschiedene Arten mit vielen unterschiedlichen
Konsequenzen berücksichtigt.*

Ein Downstream-Team kann hilflos sein, vollständig den
Upstream-Prioritäten ausgeliefert. Währenddessen kann das
Upstream-Team blockiert sein, weil es sich Sorgen macht, dass
Downstream-Systeme gebrochen werden. Die Probleme des Downstream-Teams
werden durch umständliche Verfahren zum Anfordern von Änderungen
über 
komplexe Genehmigungsprozesse nicht geringer. Und die ungehinderte
Entwicklung des Upstream-Teams wird gestoppt, wenn das Downstream-Team
ein Vetorecht bei Änderungen hat.

Daher:

**Etabliere eine klare
Customer-Supplier-Beziehung zwischen den 
beiden Teams, d.h. Downstream-Prioritäten fließen in die
Upstream-Planung ein. Verhandel und budgetiere Aufgaben für die
Downstream-Anforderungen, so dass jeder die Verpflichtungen und den
Zeitplan versteht.**

Agile Teams können das Downstream-Team bei der Planung die Rolle des
Kunden gegenüber dem Upstream-Team spielen lassen. Gemeinsam
entwickelte automatisierte Akzeptanztests können die erwartete
Schnittstelle vom Upstream validieren. Das Hinzufügen dieser Tests
zur Testsuite des Upstream-Teams, die im Rahmen der [Continuous Integration](#continuous-integration) 
ausgeführt wird, befreit das Upstream-Team bei
Änderungen von der Angst, unbeabsichtigte Auswirkungen auf Downstream
zu haben.

## Conformist {#conformist}

*Dt.: Konformist*

Wenn zwei Entwicklungsteams eine Upstream/Downstream-Beziehung haben,
in der Upstream keine Motivation hat, den Bedürfnissen des
Downstream-Teams zu entsprechen, ist das Downstream-Team hilflos.
Altruismus mag Upstream-Entwickler motivieren, Versprechungen zu
machen, aber sie werden wahrscheinlich nicht erfüllt werden. Der
Glaube an diese guten Absichten führt dazu, dass das
Downstream-Team auf der Grundlage von Funktionalitäten plant, die nie
verfügbar sein werden. Das Downstream-Projekt wird sich verzögern, bis
das Team schließlich lernt, mit dem zu leben, was ihm gegeben wird.
Eine auf die Bedürfnisse des Downstream-Teams zugeschnittene
Schnittstelle ist nicht in Sicht.

Daher:

**Eliminiere die Komplexität der Übersetzung zwischen [Bounded Contexts](#bounded-context), indem du dich sklavisch an das Modell des
Upstream-Teams
hälst. Obwohl dies den Stil der Downstream-Designer einengt und
wahrscheinlich nicht das ideale Modell für die Anwendung ergibt,
vereinfacht Konformität die Integration enorm. Außerdem
wirst du dir
eine [Ubiquitous Language](#ubiquitous-language) mit dem
Upstream-Team teilen. Upstream
hat das Sagen, daher ist es gut, die Kommunikation für sie
möglichst einfach zu gestalten. Altruismus kann ausreichen, um sie
dazu zu bringen, Informationen mit dir zu teilen.**

## Anticorruption Layer {#anticorruption-layer}

*Dt.: Antikorruptionsschicht*

Übersetzungsschichten können einfach, ja sogar elegant sein, wenn es
darum geht, gut gestaltete [Bounded Context](#bounded-context)
kooperativer Teams zu
verbinden. Aber wenn die Kontrolle oder die Kommunikation nicht
ausreicht, um einen [Shared Kernel](#shared-kernel), eine
[Partnership](#partnership) oder [Customer/Supplier](#customer-supplier)-Beziehung zu erreichen, wird die Übersetzung
komplexer. Die
Übersetzungsschicht nimmt eher einen defensiven Charakter an.

Eine große Schnittstelle mit einem Upstream-System kann am Ende
die Absicht des Downstream-Modells insgesamt überfordern, so
dass das Modell ad hoc an das Modell des anderen Systems angeglichen
wird. Die Modelle von Altsystemen sind in der Regel schwach (wenn
nicht sogar [Big Balls of Mud](#big-ball-of-mud)), und selbst wenn das
Modell
ausnahmsweise gut gestaltet ist, mag es nicht den Anforderungen des
aktuellen Projekts entsprechen, so dass es unpraktisch wäre,
sich an das Upstream-Modell anzupassen. Dennoch kann die Integration
für das Downstream-Projekt sehr wertvoll oder sogar erforderlich sein.

Daher:

**Erstelle als Downstream-Client eine Isolationsschicht, um deinem
System die Funktionalität des Upstream-Systems in Form deines eigenen
Domänenmodells zur Verfügung zu stellen. Diese Schicht spricht mit
dem anderen System über seine bestehende Schnittstelle und erfordert
wenig oder gar keine Änderungen am anderen System. Intern übersetzt
die Schicht je nach Bedarf in eine oder beide Richtungen zwischen
den beiden Modellen.**

## Open-host Service {#open-host-service}

*Dt.: Offen angebotener Dienst*

*Typischerweise definierst du für jeden [Bounded Context](#bounded-context) eine
Übersetzungsschicht für jede Komponente, mit der du integrieren musst
und die außerhalb des Kontextes liegt. Wenn jede Integration anders
ist, vermeidet dieser Ansatz mit einer Übersetzungsschicht für jedes
externe System die Korruption der Modelle mit minimalen
Kosten. Wenn dein Subsystem jedoch stark nachgefragt ist, benötigst
du möglicherweise einen flexibleren Ansatz.*

Wenn ein Subsystem mit vielen anderen integriert werden muss, kann die
Anpassung der Übersetzungsschicht für jede einzelne Integration das Team
dazu bringen sich zu verzetteln. Es gibt immer mehr zu warten und
immer mehr zu beachten, wenn Änderungen vorgenommen werden.

Daher:

**Definiere ein Protokoll, das den Zugriff auf dein Subsystem als eine
Menge von [Services](#service) ermöglicht. Öffne das Protokoll, so dass
alle, die sich mit dir integrieren müssen, das Protokoll nutzen
können.  Verbessere
und erweitere das Protokoll, um neue Integrationsanforderungen zu
erfüllen, es sei denn, ein einzelnes Team hat eigenartige
Anforderungen. Verwende dann eine spezifische Übersetzungsschicht, um das
Protokoll für diesen speziellen Fall zu erweitern, so dass das
gemeinsame Protokoll einfach und kohärent bleibt.**

Damit befindet sich der Anbieter des Service in der Upstream-Position.
Jeder Client ist Downstream, und typischerweise sind einige von ihnen
[Conformist](#conformist) und andere bauen [Anticorruption Layer](#anticorruption-layer). Ein Kontext
mit einem Open Host Service kann zudem jede Art von Beziehung zu anderen
Kontexten haben, die nicht solche Clients sind.

## Published Language {#published-language}

*Dt.: veröffentlichte Sprache*

*Die Übersetzung zwischen den Modellen zweier [Bounded
Contexts](#bounded-context)
erfordert eine gemeinsame Sprache.*

Die direkte Übersetzung in und aus den bestehenden Domänenmodellen
ist möglicherweise keine gute Lösung. Diese Modelle können übermäßig
komplex oder schlecht aufgeteilt sein. Sie sind wahrscheinlich
undokumentiert. Wenn eines dieser Modelle als Datenaustauschsprache
verwendet wird, 
wird es im Wesentlichen eingefroren und kann nicht auf neue
Entwicklungsbedürfnisse reagieren.

Deshalb:

**Verwende eine gut dokumentierte gemeinsame Sprache, welche die notwendigen
Domäneninformationen als gemeinsames Kommunikationsmedium ausdrückt
und übersetze nach Bedarf in diese Sprache bzw. aus dieser Sprache.**

Viele Branchen definieren Published Languages
in Form von 
Datenaustauschstandards. Projektteams entwickeln aber auch ihre
eigenen für den Einsatz in ihrem Unternehmen.

Published Language wird oft mit [Open Host Service](#open-host-service) kombiniert.

## Separate Ways {#separate-ways}

*Dt.: Getrennte Wege*

Wir müssen rücksichtslos sein, wenn es um die Definition von
Anforderungen geht. Wenn zwei Mengen von Funktionalitäten keine
signifikante Beziehung zueinander haben, können sie vollständig
voneinander getrennt werden.

Integration ist immer teuer, und manchmal ist ihr Nutzen gering.

Daher:

**Definiere, dass ein [Bounded Context](#bounded-context) gar keine
Verbindung zu den
anderen hat, so dass Entwickler einfache, spezialisierte Lösungen in
diesem kleinen Bereich finden können.**

## Big Ball of Mud {#big-ball-of-mud}

*Dt.: Große Matschkugel*

Wenn wir bestehende Softwaresysteme untersuchen und versuchen zu
verstehen, wie unterschiedliche Modelle innerhalb definierter Grenzen
angewendet werden, finden wir Teile von Systemen, oft große, in denen
Modelle gemischt sind und Grenzen inkonsistent sind.

Es ist leicht, beim Versuch festzufahren, die Kontextgrenzen
von Modellen in Systemen zu beschreiben, in denen es einfach keine
Grenzen gibt.

Gut definierte Kontextgrenzen entstehen erst durch intellektuelle
Entscheidungen und soziale Kräfte (auch wenn die Personen, welche die
Systeme schaffen, sich dieser Ursachen zu dem jeweiligen Zeitpunkt
nicht immer bewusst
waren). Wenn diese Faktoren fehlen oder verschwinden, vermischen sich
mehrere konzeptionelle Systeme und machen Definitionen und Regeln
mehrdeutig oder widersprüchlich. Die Systeme beginnen nach einer unvorhergesehenen Logik zu funktionieren, wenn Funktionalitäten hinzugefügt
werden. Abhängigkeiten durchziehen die Software kreuz und quer. Ursache und Wirkung
werden immer schwieriger nachvollziehbar. Schließlich erstarrt die
Software zu einer grossen Matschkugel.

Ein solcher Big Ball of Mud ist für einige Situationen tatsächlich recht
praktisch (wie im Originalartikel von Foote und Yoder beschrieben),
aber er verhindert fast vollständig die Subtilität und Präzision, die
für nützliche Modelle erforderlich ist.

{pagebreak}

Deshalb:

**Ziehe eine Grenze um das gesamte Durcheinander und bezeichne es
als einen Big Ball of Mud. Versuche nicht, in
diesem Kontext eine
ausgeklügelte Modellierung anzuwenden. Sei auf der Hut vor der
Tendenz, dass sich solche Systeme in andere Kontexte ausbreiten.**

(siehe
  [http://www.laputan.org/mud/mud.html](http://www.laputan.org/mud/mud.html), Brian Foote und Joseph Yoder)

*Big Ball of Mud ist ein neuer Begriff, der seit dem Buch von 2004 entstanden ist.*
