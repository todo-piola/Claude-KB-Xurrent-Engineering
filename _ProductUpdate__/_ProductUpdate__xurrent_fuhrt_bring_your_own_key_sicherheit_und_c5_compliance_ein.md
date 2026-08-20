---
title: "Xurrent: BYOK-Sicherheit und C5-Compliance"
date: "January 15, 2025"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/xurrent-fuhrt-bring-your-own-key-sicherheit-und-c5-compliance-ein"
slug: "xurrent-fuhrt-bring-your-own-key-sicherheit-und-c5-compliance-ein"
---

# Xurrent: BYOK-Sicherheit und C5-Compliance

Seit seiner Gründung vor über einem Jahrzehnt hat Xurrent kompromisslose Standards in den Bereichen Datenschutz, Sicherheit und Compliance aufrechterhalten.

Seit dem Inkrafttreten der [Datenschutz-Grundverordnung (DSGVO](https://www.xurrent.com/gdpr-compliance)) der Europäischen Union im Jahr 2018 bis heute ist Xurrent führend in der Bereitstellung erstklassiger Funktionen, die unseren Kunden dabei helfen, die Compliance zu wahren. Intern haben wir die [Normen ISO 27001:2022 und ISO 27018](https://www.xurrent.com/press-release/xurrent-achieves-iso-270012022-and-iso-27018-recertification) rezertifiziert und damit unser unerschütterliches Engagement für Sicherheit und Datenschutz weiter unterstrichen.

Allerdings hören wir niemals auf ….

### BYOK und C5 sind bei Xurrent angekommen

**Seit dem 1. Januar 2025 bieten wir in unserem Cloud-Rechenzentrum die Möglichkeit, „Bring Your Own Key“ (BYOK) zu nutzen.**

Ab diesem Monat können Kunden ihre Daten mit ihren eigenen privaten Schlüsseln in unserer AWS-Cloud-Bereitstellung verschlüsseln.

BYOK, so glauben wir, wird für SaaS-Organisationen zum entscheidenden Faktor werden. Mit der Aufnahme durch Xurrent wird unsere Position als Marktführer weiter gefestigt – wir sind unseren Mitbewerbern mehrere Schritte voraus, ideal für alle, die eine wirklich sichere ITSM-Plattform suchen.

Die Europäische Union und ihre Mitgliedstaaten ebnen weiterhin den Weg für die Einhaltung von Sicherheitsvorschriften und legen die Messlatte hoch. Der Cloud Computing Compliance Criteria Catalog (C5) wird bald für SaaS-Anbieter verpflichtend sein. Unsere eigenen C5-Attestierungsprüfungen sind nun im Gange, basierend auf der Verfügbarkeit dieser Funktion.

Wie funktioniert das alles?

### Das Wesentliche (die technische Seite) von BYOK und C5

Zunächst einmal ist Xurrent ein zertifizierter Amazon-Partner, und unsere in AWS gehostete Cloud nutzt den [AWS Key Management Service (KMS)](https://aws.amazon.com/kms/)als Kernkomponente für die BYOK-Implementierung. AWS KMS bietet eine sichere und skalierbare Plattform für die Verwaltung von Verschlüsselungsschlüsseln, einschließlich der Option für Kunden, ihre _eigenen_ Schlüssel einzubringen … BYOK, wenn Sie so wollen.

Lassen Sie uns etwas technischer werden.

Mit BYOK können Xurrent-Kunden ihr eigenes Amazon-Konto erstellen und ihre Customer Master Keys (CMKs) innerhalb von AWS KMS generieren (und verwalten). Diese CMKs werden zum Verschlüsseln und Entschlüsseln von Kundendaten verwendet, die auf der Xurrent-Plattform gespeichert sind. Der Kunde – und das ist der Schlüssel (Wortspiel beabsichtigt) – definiert innerhalb von AWS Identity and Access Management (IAM) differenzierte Zugriffssteuerungsrichtlinien, um den Zugriff auf die CMKs zu regeln. Dadurch wird sichergestellt, dass nur autorisierte Dienste (d. h. die Xurrent-Plattform) die Schlüssel für Verschlüsselungs- und Entschlüsselungsvorgänge verwenden können.

Darüber hinaus können Kunden AWS CloudTrail und Amazon CloudWatch so konfigurieren, dass wichtige nutzungs- und sicherheitsbezogene Ereignisse innerhalb von AWS KMS überwacht werden. Dadurch können unbefugte Zugriffsversuche oder verdächtige Aktivitäten in Echtzeit erkannt werden. Kunden haben die vollständige Kontrolle über den Widerruf von Schlüsseln. Danach sind alle mit diesen Schlüsseln verschlüsselten Daten innerhalb der Xurrent-Plattform nicht mehr verfügbar/lesbar. Darüber hinaus können Kunden Schlüssel gemäß ihren internen Richtlinien rotieren lassen.

**BONUS: All dies,**_ohne dass die Benutzererfahrung oder die blitzschnelle Leistung, die Kunden von Xurrent gewohnt sind, beeinträchtigt werden._
