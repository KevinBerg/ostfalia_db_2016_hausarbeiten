# Von der Vermutung bis hin zum Beweis und die Auswirkung auf die Praxis
In diesem Abschnitt werden das CAP-Theorem von der Vermutung hin zum Beweis und die Auswirkung auf die Praxis dargestellt.

Das CAP-Theorem wird unter anderem auch als Brewer-Theorem bezeichnet. In der theoretischen Informatik besagt es, dass ein verteiltes Computersystem unmöglich zur gleichen Zeit die Konsistenz, die Verfügbarkeit und die Ausfalltoleranz sicherstellen kann. Im Jahr 2012 erläuterte Brewer seine eigene Darstellung sowie das Konzept der „2 von 3“ Eigenschaften des CAP unrealistisch und zur falschen Anwendung führen kann [12].

Die eigene Darstellung des Berkeley Computerwissenschaftler Eric Brewer erschien erstmals im Herbst 1998, laut der „University of California“. Im Jahr 1999 wurde das CAP-Prinzip veröffentlicht. Die Vermutung von Eric Brewer wurde bei dem Symposium on Principles of Distributed Computing (PODC) im Jahr 2000 aufgezeigt. Brewer stellte das CAP-Theorem im Rahmen eines Web-Services dar [13].

Der formelle Nachweis der Vermutung von Brewer wurde im Jahr 2002 von Seth Gilbert und Nancy Lynch vom Massachusetts Institute of Technology (MIT) bekannt gegeben. Dadurch wurde aus der Vermutung der Ausdruck Theorem [14].

Brewer wollte darstellen, aus welchem Grund die Konsistenz, die Verfügbarkeit und die Ausfalltoleranz nicht gleichzeitig zu vereinen sind. Seine Erkenntnis zeigte auf, dass nur 2 der 3 Eigenschaften zur selben Zeit zu erzielen sind. Im Folgenden werden die jeweils zwei kombinierten Eigenschaften bzw. die Klassifizierung von Datenbanktechnologien gemäß CAP näher beschrieben.

## Klassifizierung von Datenbanktechnologien gemäß CAP
Die Einteilung erfolgt bezüglich der Eigenschaften in CP, AP und CA Systeme.

### CP
Eine Netzpartition bezeichnet den Zustand bei einem gleichzeitigen Ausfall aller Netzwerkverbindungen zwischen zwei Systemgruppen [15].

CP bezieht sich auf die Consistency (Konsistenz) und Partition tolerance (Ausfalltoleranz). CP-Systeme antworten auf eine Netzwerkpartition mit dem Verzicht auf eine vollständige Verfügbarkeit. Die Verfügbarkeit bezieht sich auf den Teil des Netzwerkes, der konsistent gehalten werden kann, somit ist der Rest nicht verfügbar. Dadurch wird die Konsistenz und die Ausfalltoleranz gewährleistet, aber nicht die Verfügbarkeit. Nachdem die Verbindung zwischen den Knoten aufgebaut ist, erfolgt der Aufbau der Konsistenz bei den nicht verfügbaren Knoten. Danach können diese wieder auf Anfragen reagieren [16].

Zu der CP-Klassifikation gehören die Banking-Anwendungen. Die Konsistenz der Daten steht bei verteilter Finanzanwendung an erster Stelle. Ein überwiesener Geldbetrag vom Konto A auf das Konto B muss zuverlässig von dem Konto A abgezogen und bei dem Konto B angezeigt werden. Demnach ist es nicht möglich, dass der Betrag auf dem Konto A abgezogen ist und nicht auf dem Konto B erscheint. Die Ausführung erfolgt entweder ganz oder gar nicht. Dies muss auch im Falle einer Störung im Datenverkehr gewährleistet werden und betrifft somit die Ausfalltoleranz. Die Verfügbarkeit bei solchen Anwendungen spielt eher eine untergeordnete Rolle. Der Geldautomat soll daher bei Netzwerkstörungen nicht verfügbar sein anstatt einen Fehler im Geschäftsabschluss zu erhalten [11].

### AP
Bei den AP-Systemen wird bei einer Netzwerkpartitionierung auf die vollständige Konsistenz verzichtet. Bei allen Teilen des Netzwerkes erfolgt eine Reaktion auf Anfragen, jedoch sind die Antworten nicht zwangsläufig konsistent. Nach Wiederherstellung der Verbindung wird die Konsistenz wiederaufgebaut. Manche AP-Systeme verzichten sogar ohne eine Netzwerkpartitionierung auf die Konsistenz und beschränken sich auf die „Eventual Consistency“. Die „Eventual Consistency“ ist eine reduzierte Form der Konsistenz und wird oft in verteilten Datenbanken verwendet. Dabei sind Datensätze in einer bestimmten Zeit wieder konsistent, wenn von Schreibvorgängen und Fehlern abgesehen werden kann. Bei Schreiboperationen werden die Daten nicht sofort auf alle Partitionen verteilt, dies erfolgt aus Performancegründen [11].

Zu den AP-Systemen gehören „Domain Name System“ (DNS), Cloud-Systeme und verteilte NoSQL-Datenbanken. Bei den DNS besteht eine hohe Verfügbarkeit sowie Toleranz bei dem Ausfall einzelner DNS-Server. Hierbei wird jedoch auf die Konsistenz verzichtet. Ein geänderter Eintrag im DNS wird erst nach einiger Zeit an die ganze DNS-Hierarchie verbreitet. Erst dann wird dies von allen Clients erkannt. Bei Cloud-Plattformen ist eine horizontale Skalierung gegeben, dabei erfolgt die Verteilung auf mehrere Knoten. Meist laufen diese nicht immer auf ausfallsicherer Hardware, deshalb müssen Anwendungen unbedingt eine Toleranz gegenüber dem Ausfall verschiedener Knoten aufweisen. Unter anderem muss eine hohe Verfügbarkeit gewährleistet werden. Zu Web-Anwendungen, die auf strenge Konsistenz verzichten, gehören z. B. Facebook und Twitter [11].

### CA
Bei den CA-Systemen wird versucht die Konsistenz und die Verfügbarkeit zu gewährleisten. In einem verteilten System muss jedoch eine Netzwerkpartitionierung beachtet werden, dementsprechend müssen auch hier zwischen Konsistenz und Verfügbarkeit Prioritäten gesetzt werden. Sinnvoll wäre daher eine Klassifizierung im CA-System in einem nicht verteilten System, jedoch ist hier eine Netzwerkpartitionierung ausgeschlossen [16].

Bei den CA-Systemen lässt sich das „Relational Database Management System“ (RDBMS) einordnen. Zu den klassischen Relationalen Datenbanken gehören Oracle, DB2 oder Microsoft SQL Server. Diese Datenbanken zielen hauptsächlich auf eine Konsistenz ab. Des Weiteren gehören RDBMS-Cluster vorwiegend zu CA-Systemen, da sie besonders zur Verfügbarkeit und Konsistenz aller Knoten tendieren. Eine untergeordnete Rolle spielt hier die Ausfalltoleranz, da vorwiegend ein Betrieb mit hochverfügbaren Netzwerken und Servern erfolgt [11].

Die Klassifizierung der Eigenschaften in CP, AP und CA Systeme ist verschönerte Darstellung. In der Praxis können die Eigenschaften jedoch nicht immer so klar getrennt werden, wie oben beschrieben. Dabei kommt es vor, dass die Grenzen verschwimmen und es auch Mischformen zwischen CP und AP Systemen geben kann. Diese Systeme können sich dann von Fall zu Fall unterschiedlich zwischen C und A festlegen [16].

In Bezug auf die Netzwerkpartitionierung können Schwierigkeiten in der Praxis auftreten. Bei dem System kann nicht sichergestellt werden, dass dieses bei einer Netzwerkpartitionierung einheitlich reagiert. Es kann vorkommen, dass manche Knoten über eine Verbindungsunterbrechung nicht in Kenntnis gesetzt sind und dieses kann ihnen auch nicht mitgeteilt werden. Eine Verbindungsunterbrechung wird in der Praxis anhand der Überschreitung von Timeouts erfasst. Es müssen jedoch nicht alle Knoten zugleich betroffen sein. Bei einer schlechten Netzwerkverbindung befindet sich das System in einem Zwischenzustand [16].

Eric Brewer erklärte in seinem Artikel „CAP Twelve Years Later: How the “Rules” Have Changed“ aus dem Jahr 2012 die Notwendigkeit, während einer Netzwerkpartitionierung, zwischen der Konsistenz und der Verfügbarkeit zu wählen. Der Entwickler entscheidet sich hier oft für die Eigenschaft Verfügbarkeit Des Weiteren stellt Brewer dar, dass Entwickler und Forscher seit der Einführung des CAP-Theorem diesen als Grund für die Erforschung einer Vielzahl von neuen verteilten Systemen angewendet haben [12].

Seth Gilbert und Nancy A. Lynch analysierten das CAP-Theorem und veröffentlichten den Artikel „Perspectives on the CAP Theorem“ im Jahr 2012. In diesem werden die theoretischen und praktischen Aspekte des CAP-Theorems dargestellt [17].

Sie beschreiben, dass Praktiker trotz der negativen Auswirkung des CAP-Theorems, verteilte Systeme erstellen können. Dabei haben sie trotzdem Erfolg bei der Entwicklung, Implementierung der Systeme und Bewältigung der Herausforderungen des CAP-Theorems [17].

Bei unzuverlässigen Netzwerken scheinen nur zwei Ansätze sinnvoll zu sein, entweder die Verfügbarkeit oder die Konsistenz aufzugeben. Die Auswirkung des CAP-Theorems zeichnet sich hier aus, indem keine Konsistenz und Verfügbarkeit in einem partitionsanfälligen Netzwerk erlangt werden kann. Ein weiterer Ansatz wird häufig in der Praxis verwendet. Ein großes System wird in mehrere Untersysteme unterteilt, jeder dieser kann einen unterschiedlichen Kompromiss wählen. Diese Segmentierung kann entlang verschiedener Dimensionen erfolgen. Für das Gesamtsystem sieht es aus, als wäre die Konsistenz und Verfügbarkeit aufgeben worden. Diese resultierende Konstruktion reagiert dennoch unter schlechten Netzwerkbedingungen auf die häufigsten Anforderungen der Benutzer und stellt ein hohes Maß an Konsistenz bereit [17].

Eine weitere Auswirkung des CAP-Theorems in der Praxis betrifft das sogenannte Cloud-Computing. Cloud-Provider haben die Interpretation des CAP-Theorems erweitert. Dabei gilt ein System als nicht verfügbar, wenn die Antwortzeit die Latenzzeit überschreitet und eine langsame Netzwerkverbindung wird als partitioniert anerkannt. Das Cloud Computing wird in der Hausarbeit noch ausführlicher dargestellt. Für die Erzielung einer hohen Skalierbarkeit und Performance ohne Knoten-zu-Knoten Koordinierung oder Synchronisation, schwächen die Entwickler die Konsistenz ab. Damit wird eine Verfügbarkeit des Systems erhalten, auch bei keinem wirklichen Netzwerkausfall [18].

In dem Artikel „Consistency Tradeoffs in Modern Distributed Database System Design“ von Daniel J. Abadi aus dem Jahr 2012 wurde aufgezeigt, dass ein verteiltes System eine synchrone Replikation häufig nicht unterstützen kann. Viele Anwendungen benötigen eine geringe Latenzzeit. Daher wird auch dann die Konsistenz aufgegeben, wenn keine Netzwerkpartition besteht. Für ein besseres Verständnis der Kompromisse des CAP-Theorems wäre ein neuer Ansatz des CAP-Theorems sinnvoll. Hierbei soll die Latenz gegenüber dem Konsistenz Kompromiss spezifischer erfolgen [19].

Die Entwicklung eines hochverfügbaren Systems, an dem die Verfügbarkeit über der Konsistenz steht, führt zu einer Erhöhung der Komplexität verteilter Systeme. Programmierer sollten die Kenntnis besitzen, wann man einen schnellen/inkonsistenten Zugang im Vergleich zu einem langsamen/konsistenten Zugang benötigt, sowohl eine hohe Leistung als auch die Korrektheit sicherzustellen. Des Weiteren muss eine Regel für die Konfliktlösung definiert sein, die den Anforderungen der Nutzer entsprechen [18].

Entwickler beschäftigten sich mit einigen Konsistenzmodellen, welche sich aus dem Kompromiss zwischen Designkomplexität und Verfügbarkeit, sowie Performance ergeben. Bei der „Eventual Consistency“ wird die Verfügbarkeit gewählt, welche Updates für jede nächstgelegene Replik erlaubt. Das System führt somit Aktualisierung im Laufe der Zeit durch. Die „Eventual Consistency“ kann jedoch nicht die gleiche Reihenfolge der Updates garantieren. Für die Lösung von Datenkonflikten werden anwendungsspezifische Regeln benötigt. Dieses „Eventual Consistency“-Konzept wurde zuerst in den frühen 1990er Jahren in den Coda, Bayou und Ficus verteilten Systemen eingesetzt [18].

Die Entwickler von Yahoo's PNUTS wählten eine stärkere Konsistenz auf Kosten der Verfügbarkeit. In dem Artikel „Overcoming CAP with Consistent Soft-State Replication“ befürworten Kenneth P. Birman und seine Koautoren eine noch stärkere Konsistenz im Rechenzentrum, in denen Partitionen selten sind. Sie zeigen auf, dass in diesem Rahmen eine geringe Latenz und Skalierbarkeit ohne die Konsistenz zu vernachlässigen erreichbar ist [18].

Letztendlich spielen die CAP Theorem seit der Einführung von Brewer weiterhin eine relevante Rolle in Bezug auf das Verständnis und der Optimierung von verteilten Systemen.

Zum Verständnis und zur Optimierung von Systemen sollten die möglichen Fehler in Datenbank bekannt sein. Im folgenden Abschnitt werden diese näher behandelt.

## Fehler in Datenbanken
Bei dem Umgang mit Datenbanksystemen ist die Kenntnis der möglichen Fehler in Datenbanken relevant. Folglich werden die Fehler in Datenbanken beschrieben und welche dieser in Bezug auf das CAP-Theorem nicht zu treffen bzw. eine Anwendung finden können.

Als erstes lassen sich die Anwendungsfehler darstellen. Hierbei führt eine Anwendung eine oder mehrere falsche Aktualisierungen durch. Dies wird meistens nicht nach Minuten oder Stunden danach entdeckt. Die Datenbank muss bis zu einem definierten Punkt vor der betreffenden Transaktion gesichert werden und die nachfolgende Aktivität wird wiederhergestellt [20].

Des Weiteren gibt es wiederholbare DBMS-Fehler. Das DBMS stürzte an einem Verarbeitungsknoten ab. Bei Ausführung der gleichen Transaktion auf einem Verarbeitungsknoten mit einer Replik, führt die Sicherung zum Absturz. Diese Fehler bezeichnet man als Bohr-Bugs [20].

Außerdem gibt es nicht wiederholbare DBMS-Fehler. Hierbei ist die Datenbank abgestürzt, jedoch ist eine Replik möglicherweise noch in Ordnung. Diese werden häufig durch seltsame Ausnahmefälle verursacht, welche die asynchronen Operationen betreffen. Diese werden Heisenbugs genannt [20].

Zu weiteren Fehlern gehören die Betriebssystemfehler. Das Betriebssystem stürzt an einem Knoten ab, erzeugt durch den „blue screen of death“ (Blauer Tod) [20].

Als nächstes wird ein Hardwarefehler in einem lokalen Cluster genannt. Dazu zählen Speicherausfälle, Festplattenfehler usw. Im Allgemeinen verursachen diese Fehler einen „Notstopp“ durch das Betriebssystem oder das DBMS. Diese treten jedoch teilweise als Heisenbugs auf [20].

Des Weiteren gibt es eine Netzwerkpartition in einem lokalen Cluster. Das LAN ist ausgefallen und die Knoten können nicht mehr miteinander kommunizieren [20].

Schließlich gibt es auch Fehler in Datenbank, die durch eine Katastrophe ausgelöst wurden. Das lokale Cluster wird durch eine Flut, Erdbeben usw. ausgelöscht. Das Cluster existiert somit nicht mehr [20].

Als letzter Punkt wird ein Netzwerkfehler in den WAN-Verbindungsclustern genannt. Das WAN ist ausgefallen und Cluster können nicht mehr alle miteinander kommunizieren [20].

Die Anwendungsfehler und wiederholbare DBMS-Fehler werden durch ein hohes Verfügbarkeitsschema verursacht. Bei diesen beiden Fehlern gibt es keine Möglichkeit fortzufahren, da die Verfügbarkeit nicht erreicht werden kann. Eine Replikkonsistenz ist daher nicht sinnvoll, da der aktuelle DBMS-Zustand fehlerhaft ist [20].

Ein Fehler in der Datenbank, ausgelöst durch eine Katastrophe, ist nur dann wiederherstellbar, wenn eine lokale Transaktion nach der Sicherung stattfindet, welche die Transaktion von einem anderen WAN-verbundenen Cluster empfängt. Wenige Anwendungsentwickler akzeptieren diese Art von Latenz. Demnach kann eine Konsistenz nicht sichergestellt werden, da eine Transaktion vollständig verloren gehen kann, wenn eine Katastrophe an einem lokalen Cluster auftritt, bevor die Transaktion an anderer Stelle erfolgreich weitergeleitet wurde. Hier muss sich der Anwendungsentwickler entscheiden, ob der Aspekt des Datenverlustes bei einer Katastrophe dem Aspekt der Leistungseinbuße, um diese zu vermeiden, überwiegt [20].

Der Anwendungsfehler, der wiederholbare DBMS-Fehler und der Fehler bei einer Katastrophe sind Beispiele die bei dem CAP-Theorem nicht zutreffen. Jedes reale System muss für den Fall der Wiederherstellung bereit sein. Das CAP-Theorem kann nicht zur Beratung angefochten werden [20].

In manchen Fällen könnte das CAP jedoch Anwendung finden. Eine Netzwerkpartition in einem lokalen Cluster ist äußerst selten, vor allem wenn das LAN repliziert wird [20].

In Anbetracht der lokalen Ausfälle, wie nicht wiederholbare DBMS-Fehler, Betriebssystemfehler, ein Hardwarefehler in einem lokalen Cluster und eine Netzwerkpartition in einem lokalen Cluster, führt die Mehrheit dazu an einem einzelnen Knoten zu scheitern. Dies ist ein degenerierter Fall einer Netzwerkpartition, die leicht durch viele Algorithmen überstanden wird. Deshalb ist es wahrscheinlich sinnvoller die Ausfalltoleranz zu vernachlässigen anstatt der Konsistenz. In einer LAN-Umgebung ist eventuell ein CA System effizienter als ein AP System wie z. B. bei neueren SQL-OLTP-Systeme (VoltDB und NimbusDB) [20].

Bezogen auf einen Netzwerkfehler in den WAN-Verbindungsclustern, ist eine Partition sehr selten, da es in den heutigen WANs genug Redundanz gibt. Lokale Fehler und Anwendungsfehler sind viel wahrscheinlicher. Außerdem ist das wahrscheinlichste WAN-Versagen, den kleinen Teil des Netzes von der Mehrheit zu trennen. Dabei kann die Mehrheit mit einfachen Algorithmen weiterarbeiten und nur der kleine Teil muss blockiert werden. Demnach wäre es nicht sinnvoll, die Konsistenz für die ganze Zeit aufzugeben im Austausch für die Verfügbarkeit einer kleinen Teilmenge der Knoten [20].

Eine Verlangsamung entweder im OS, im DBMS oder im Netzmanager, kann durch schiefe Lage, Pufferpool Aspekten oder weiteren Gründen verursacht werden. Es muss entschieden werden, welche fehlerhaften Komponenten entfernt werden müssen. Zum Beispiel wird die langsame Antwortzeit gegen einen anderen vorhergehenden Fehler umgewandelt [20].

Demnach sollte die Software so geschrieben werden, dass sie mit Belastungsspitzen umgehen kann, ohne zu scheitern. Dies könnte durch Lastablagerung und das Arbeiten in einem herabgesetzten Modus erfolgen. Eine gute Monitoring-Software unterstützt dabei die Probleme frühzeitig zu erkennen, da das Hinzufügen von Kapazität eine relevante Lösung ist. Eine selbst-rekonfigurierende Software, die zusätzliche Ressourcen schnell aufnehmen kann, wäre ein sinnvoller Lösungsansatz [20].

Letztlich sollte die Konsistenz nicht zu schnell außer Acht gelassen werden, da es Fehlerfälle gibt, bei denen CAP nicht angewendet werden kann [20].

## Auswirkungen des CAP-Theorems auf Cloud Computing
Bevor nun auf die Auswirkungen des CAP Theorems auf das Cloud Computing eingegangen wird, soll zunächst der Begriff Cloud Computing näher beleuchtet werden. Cloud Computing dient in der IT-Branche dazu IT-Infrastrukturen auszulagern. Dabei sollen die Ressourcen, die benötigt werden, vom Anbieter dynamisch zur Verfügung gestellt werden. Einen Einblick in den genauen Aufbau dieser Cloud bekommt der Kunde nicht, dieser bleibt in der Virtualisierungsschicht verborgen. Der Kunde bekommt lediglich den Service zur Verfügung gestellt, die Prozesse im Hintergrund sieht er dabei nicht [21].

Große Unternehmen, wie Google oder Amazon, sind darauf angewiesen, Systeme zu betreiben, die eine große Anzahl an Ressourcen aufweisen, um Spitzenlasten abfangen zu können. Zu Normallastzeiten werden diese jedoch nicht voll ausgelastet, weshalb viele Unternehmen ihre freien Ressourcen vermieten [21].

Zu den Prinzipien des Cloud Computings zählt vor allem die dynamische Verfügbarkeit (CPU-Zeit, Speicherplatz). Dem Kunden sollen im Alltag Aufgaben abgenommen werden können, indem Prozesse wie das Starten und Stoppen von Rechnersystemen, das Erstellen von Backups oder die Software-Installation automatisiert werden. Man bedient sich dann dem Ansatz der Virtualisierung, um Ressourcen dynamisch zuweisen zu können. Server werden hierbei zu Server-Farmen zusammengeschlossen, um darauf den Betrieb der virtuellen Maschinen zu tätigen. Diese Maschinen sind dann frei skalierbar in ihren Ressourcen. Neu an diesem Ansatz ist, dass die hierbei verwendete Software komplett an die Gegebenheiten angepasst ist. Dies bedeutet, dass die virtuellen Maschinen frei verschiebbar und skalierbar innerhalb des gesamten Serververbundes sind und nicht mehr nur innerhalb eines Servers. Dadurch können die Ressourcen enorm vergrößert werden. Um die Services einzusetzen, stehen dem Kunden also sehr viele Ressourcen zur Verfügung. Die Vergabe der Ressourcen findet hierbei vollkommen dynamisch statt und ist zudem linear skalierbar. Das heißt, wenn ein Kunde zusätzliche Ressourcen braucht, kann die Maschine über mehrere physikalische Einheiten hinweg handeln. Wenn der Bedarf dann sinkt, können die Ressourcen wiederum freigegeben werden [21].

Ein weiteres Prinzip stellt das sogenannte „Pay-as-you-grow/go“ dar. Hierbei wird vom Kunden grundsätzlich nur für die Dienste bezahlt, die er tatsächlich benötigt hat. Die Einheit der Abrechnung richtet sich dabei meist nach der CPU-Zeit in Stunden oder in Gigabyte für den Netzwerkverkehr und Speicherbedarf [21].

Beim Cloud Computing unterscheidet man des Weiteren verschiedene Service-Modelle. Zum einen wird hier unterschieden in „Infrastructure as a Service“ (IaaS). Dabei handelt es sich um die Bereitstellung von IT-Infrastruktur auf visualisierte Weise via Internet. Der jeweilige Kunde nutzt hierbei das Netzwerk, den Server sowie Storage und weitere Rechenzentrumsinfrastruktur als Service über das Internet. Zum anderen beschreibt der Begriff „Platform as a Service“ (PaaS) die Bereitstellung der gesamten Anwendungssoftware oder der Anwendungs-Infrastruktur in Form von technischen Frameworks wie Datenbanken und Middleware. Eine weitere Ebene wird als „Software as a Service“ (SaaS) bezeichnet. Hierbei beziehen die Nutzer eine Applikation über das Internet, wobei die Applikation und die Ressourcen der Infrastruktur zu einem „Gesamtbündel“ kombiniert werden. Zuletzt wird differenziert in den „Business Process as a Service“ (BPaaS). Dies umschreibt eine bestimmte Art Cloud Computing, bei der die Geschäftsprozesse ausgelagert werden können mit Hilfe der Clouds [22].

Desweiteren kann man Clouds hinsichtlich ihrer Organisationsform unterscheiden, womit die Art der Nutzung und Bereitstellung gemeint ist. Zum einen existiert hier die sog. „Private Cloud“ (Pv), welche eine betriebsinterne Umgebung mit beschränktem Zugang (für das Unternehmen, autorisierte Partner/ Lieferanten/ Kunden) darstellt. Zum anderen besteht die Möglichkeit einer „Public Cloud“ (Pu). Sie wird von IT-Dienstleistern betrieben und über das Internet zur Verfügung gestellt. Dabei teilen sich Unternehmen häufig eine virtualisierte Infrastruktur. Die Umgebung bietet die Möglichkeit einer schnellen und flexiblen Nutzung. Die Pu bietet Anwendungs- und Geschäftsprozesse sowie Infrastruktur-Services von hohem Standard. Desweiteren gibt es die „Hybrid Clouds“ (H), welche Kombinationen aus Public Clouds, Private Clouds und der herkömmlichen IT-Umgebung bieten. Zuletzt wird unterschieden in die sogenannten „Community Clouds“ (Co). Sie werden auch als „Vertical (Application) Clouds“ bezeichnet und stellen eine Ausprägung der Private Clouds dar. Dabei werden spezielle branchenspezifische Anwendungsbausteine auf der SaaS-Ebene für eine bestimmte Gruppe von Unternehmen mit ähnlichen Anforderungen bereitgestellt [22].

Innerhalb der letzten Jahre konnte der Markt für Cloud Computing ein starkes Wachstum verzeichnen. Demnach werden derzeit von zehn Prozent der deutschen Unternehmen Public Clouds und von 34 Prozent Private Clouds verwendet (Stand 2013) [22].

Die Vorteile liegen hierbei vor allem in der gesteigerten Flexibilität und der Einsparung von Kosten, aber auch in der Auslagerung der Verantwortung und Wartung an den Anbieter, sowie der hohen Skalierbarkeit der Ressourcen [23].

Hinsichtlich des CAP Theorems sind bei Cloud Computing verschiedene Aspekte zu berücksichtigen. Da die Clouds auf eine horizontale Skalierung setzen (das heißt die Last wird auf viele Knoten verteilt), müssen diese Anwendungen unbedingt eine Toleranz gegenüber Ausfällen von einzelnen Knoten besitzen. Ebenso wird eine hohe Verfügbarkeit gefordert, da Anwender oftmals kein Verständnis für lange Wartezeiten hat und dadurch schnell gewillt ist zur Konkurrenz zu wechseln. Somit fallen Cloud-Anwendungen zu großen Teilen in die Kategorie „AP“ [9].

Dies bedeutet nun, dass man sich mit schwächeren Konsistenzbedingungen abfinden muss. Das ist darin begründet, dass aufgrund des CAP Theorems die Konsistenz in diesem Fall nicht gewährleistet werden kann. In den meisten Fällen ist die schwächere Konsistenz jedoch absolut ausreichend. Lediglich eine vollkommen inkonsistente Datenhaltung wäre nicht zielführend [9].