---
title: Połączone środowisko w Visual Studio
description: Połączone środowisko łączy się z Internetem z maszyny klienckiej i zapewnia usługę klientowi.
ms.date: 05/20/2021
ms.topic: conceptual
helpviewer_keywords: ''
author: SayyedaM
ms.author: sayyedamussa
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.openlocfilehash: 689fc40be8aee959023777a3fac6d9134ee979ea
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222893"
---
# <a name="connected-experiences-in-visual-studio"></a>**Połączone środowisko w Visual Studio** #

Visual Studio składa się z aplikacji klienckich i połączonych funkcji zaprojektowanych w celu umożliwienia bardziej efektywnego code. Przykłady [połączonych NuGet](/nuget/consume-packages/install-use-packages-visual-studio) to aktualizowanie pakietu narzędzi, wybieranie sugestii [](/visualstudio/liveshare/quickstart/share) [funkcji IntelliCode](/visualstudio/intellicode/overview) i Live Share z innym deweloperem. 

## <a name="choose-whether-these-connected-experiences-are-available-to-use"></a>Wybierz, czy te połączone środowisko jest dostępne do użycia ##

Możesz wybrać połączone środowisko do użycia. Korzystanie z niektórych połączonych funkcji wymaga umowy z różnymi i dodatkowymi warunkami umowy licencyjnej Visual Studio EULA. Te doświadczenia mogą być własnością firmy Microsoft Usługi online i/lub usługami należącymi do innych firm. Na przykład w przypadku korzystania z połączonych funkcji usługi GitHub [GitHub](https://docs.github.com/github/site-policy/github-privacy-statement) będą stosowane zasady zachowania [](https://docs.github.com/github/site-policy/github-corporate-terms-of-service)poufności informacji i warunki użytkowania usługi [](https://docs.github.com/github/site-policy/github-additional-product-terms) [GitHub,](https://docs.github.com/github/site-policy/github-terms-of-service)firmowe warunki użytkowania usługi GitHub i/lub dodatkowe postanowienia dotyczące produktu. W przypadku [zgłoszenia problemu użytkownik](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)zgadza się na warunki użytkowania firmy [Microsoft](https://www.microsoft.com/legal/terms-of-use) i zasady zachowania poufności informacji [firmy Microsoft.](https://privacy.microsoft.com/en-us/privacystatement) Jeśli korzystasz z usługi NuGet, wyrażasz zgodę na warunki [NuGet](https://www.nuget.org/policies/Terms) użytkowania oraz Oświadczenie [o ochronie prywatności firmy Microsoft.](https://privacy.microsoft.com/en-us/privacystatement) 

Podczas instalowania Visual Studio można opcjonalnie wybrać [obciążenia i składniki do zainstalowania.](/visualstudio/install/install-visual-studio) Obciążenia i składniki mogą korzystać z oprogramowania innych firm i mogą włączać połączone środowisko w zależności od ich funkcjonalności. Na przykład [pobranie pakietu roboczego Tworzenie aplikacji na platformie Azure umożliwia publikowanie aplikacji w chmurze na platformie Azure.](https://visualstudio.microsoft.com/vs/features/azure/) W zależności od wybranych opcji instalacji można również użyć menu Narzędzia i opcje, aby nawiązać połączenie, skonfigurować i korzystać z połączonych funkcji. Możesz na przykład nawiązać połączenie z serwerem, dodać uwierzytelnianie usług platformy Azure lub zmienić ustawienia funkcji IntelliCode lub LiveShare.  

Możesz również użyć ustawień zapory [organizacji, aby](/visualstudio/install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server) włączyć lub wyłączyć połączenie z usługami. Należy pamiętać, że wyłączenie połączenia z punktem końcowym może negatywnie wpłynąć na wydajność powiązanych Visual Studio końcowych. 

Ponadto platforma Visual Studio Marketplace oferuje rozszerzenia, które mogą umożliwiać środowisko połączone z usługami firmy lub innych firm. Visual Studio Witryna Marketplace podlega niniejszym [Visual Studio marketplace](https://cdn.vsassets.io/v/M146_20190123.39/_content/Microsoft-Visual-Studio-Marketplace-Terms-of-Use.pdf) oraz oświadczeniu o ochronie prywatności w [firmie Microsoft.](https://privacy.microsoft.com/en-us/privacystatement) Każde rozszerzenie wymaga umowy dotyczącej określonych warunków użytkowania i zasad zachowania poufności informacji skojarzonych z tą ofertą.  


## <a name="required-service-data"></a>Wymagane dane usługi ##

Wymagane dane usługi mogą zawierać informacje związane z działaniem połączonego połączenia, które są potrzebne do zapewnienia bezpieczeństwa i aktualnej podstawowej usługi oraz jej działania zgodnie z oczekiwaniami. Jeśli zdecydujesz się na użycie połączonego środowisko, które analizuje zawartość, na przykład IntelliCode, kod wybrany dla modelu jest również wysyłany i przetwarzany, aby zapewnić połączone środowisko. Wymagane dane usługi mogą również zawierać informacje wymagane przez połączone środowisko do wykonania zadania, takie jak aktualizowanie NuGet pakietu. Wymagane dane usługi można zarządzać, wybierając, czy chcesz używać określonej usługi. Jeśli nie używasz usługi, nie są zbierane żadne wymagane dane usługi. 

Wymagane dane usługi różnią się od danych diagnostycznych, ponieważ dane diagnostyczne odnoszą się do oprogramowania uruchomionego na urządzeniu. Wybór uczestnictwa w programie [Visual Studio Program poprawy jakości obsługi klienta (VSCEIP)](/visualstudio/ide/visual-studio-experience-improvement-program)kontroluje ustawienia prywatności danych diagnostycznych, ale to ustawienie nie ma wpływu na to, czy wymagane dane usługi są wysyłane. 

## <a name="diagnostic-data-collection"></a>Zbieranie danych diagnostycznych ##

Dane diagnostyczne są używane do Visual Studio i aktualnych, wykrywania, diagnozowania i rozwiązywania problemów, a także do udoskonaleń produktu. Dane diagnostyczne są zbierane i wysyłane do firmy Microsoft Visual Studio oprogramowania klienckiego uruchomionego na urządzeniu użytkownika.

Rezygnacja z opcjonalnego zbierania danych diagnostycznych jest rezygnacją. Niektóre kolekcje danych diagnostycznych są wymagane w celu Visual Studio, że dane są bezpieczne, aktualne i działa zgodnie z oczekiwaniami. Wybór rezygnacji z programu [VSCEIP](/visualstudio/ide/visual-studio-experience-improvement-program)nie będzie mieć wpływu na zbieranie wymaganych danych diagnostycznych. 
