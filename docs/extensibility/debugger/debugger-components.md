---
title: Składniki debugera | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28afdd7f12e7d83b042f5c705c85fa567fdbb979
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345889"
---
# <a name="debugger-components"></a>Składniki debugera
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugera jest zaimplementowany jako pakietu VSPackage i zarządza cały debugowanie. Sesja debugowania obejmuje następujące elementy:

- **Pakiet debugowania:** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugera zawiera ten sam interfejs użytkownika, niezależnie od tego, co jest debugowany.

- **Menedżer debugowania sesji (SDM):** Zapewnia spójny interfejs programistyczny do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugera dla zarządzania szereg aparaty debugowania. Jest implementowana przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- **Menedżer debugowania procesów (menedżerów PDM):** Zarządza dla wszystkich uruchomionych wystąpieniach [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], listę wszystkich programów, które mogą być lub są debugowane. Jest implementowana przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- **Debugowanie aparatu (DE):** Jest odpowiedzialny za monitorowanie debugowanego programu komunikacji stan uruchomionego programu SDM i menedżerów PDM oraz interakcji z nimi Ewaluator wyrażeń i dostawca symboli, aby przeprowadzać analizę w czasie rzeczywistym stanu programu pamięci i zmienne. Jest implementowana przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (dla języków, obsługuje on) i dostawców innych firm, którzy mają być obsługiwane ich w czasie wykonywania.

- **Ewaluator wyrażeń (EE):** Obsługuje dynamiczne szacowanie zmiennych i wyrażeń, dostarczone przez użytkownika, gdy program został zatrzymany w określonym punkcie. Jest implementowana przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (dla języków, obsługuje on) i od innych dostawców, którzy mają być obsługiwane w ich własnym języku.

- **Dostawca symboli (SP):** Nazywane również obsługi symboli, mapuje symbole debugowania programu uruchomionego wystąpienia programu tak, aby istotne informacje, można podać (takie jak debugowanie na poziomie kodu źródłowego i Obliczanie wyrażenia). Jest implementowana przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (Aby uzyskać środowisko uruchomieniowe języka wspólnego [CLR] symboli i bazy danych programu [PDB] symboli format pliku), jak również od innych dostawców, którzy mają własne własności sposób przechowywania informacji o debugowaniu.

  Na poniższym diagramie przedstawiono relację między tymi elementami debugera programu Visual Studio.

  ![Przegląd składników debugowania](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")

## <a name="in-this-section"></a>W tej sekcji
 [Pakiet debugowania](../../extensibility/debugger/debug-package.md) w tym artykule omówiono debugowanie pakietu, który jest uruchamiany w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] powłoki i obsługuje cały interfejs użytkownika.

 [Menedżer debugowania procesów](../../extensibility/debugger/process-debug-manager.md) zawiera omówienie funkcji menedżerów PDM, czyli menedżera procesów, które mogą być debugowane.

 [Menedżer debugowania sesji](../../extensibility/debugger/session-debug-manager.md) definiuje SDM, co zapewnia spójny widok sesji debugowania środowiska IDE. SDM zarządza DE.

 [Aparat debugowania](../../extensibility/debugger/debug-engine.md) dokumenty debugowania usług, które zapewnia DE.

 [Tryby operacyjne](../../extensibility/debugger/operational-modes.md) zawiera omówienie trzech trybów, w których może działać IDE: projektowania trybu, tryb uruchamiania i trybie przerwania. Omówiono także mechanizmów przejścia.

 [Ewaluator wyrażeń](../../extensibility/debugger/expression-evaluator.md) zawiera wyjaśnienie przeznaczenia EE w czasie wykonywania.

 [Dostawca symboli](../../extensibility/debugger/symbol-provider.md) w tym artykule omówiono, jak to zrobić, na wdrażanie, dostawca symboli ocenia zmiennych i wyrażeń.

 [Typ wizualizatora i Przeglądarka niestandardowa](../../extensibility/debugger/type-visualizer-and-custom-viewer.md) Discusses Wizualizator typów i Przeglądarka niestandardowa są i jaką rolę Ewaluator wyrażeń odgrywa w obsłudze, obu.

## <a name="related-sections"></a>Sekcje pokrewne
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md) opisano główne pojęcia dotyczące architektury debugowania.

 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md) wyjaśnia, jak DE działa jednocześnie w kontekstach oceny kodu, dokumentację i wyrażenia. W tym artykule opisano, dla każdego z trzech kontekstów, lokalizacji, pozycja lub oceny odpowiednie do niego.

 [Debugowanie zadań](../../extensibility/debugger/debugging-tasks.md) zawiera łącza do różnych zadań debugowania, takich jak uruchamianie programu i wyrażeń.

## <a name="see-also"></a>Zobacz także
- [Wprowadzenie](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)