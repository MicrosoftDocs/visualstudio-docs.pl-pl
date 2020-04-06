---
title: Składniki debugera | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03c400fd03c5ee0f2629e9f436b65f53f8f2ac8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739009"
---
# <a name="debugger-components"></a>Składniki debugera
Debuger [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jest zaimplementowany jako VSPackage i zarządza całą sesją debugowania. Sesja debugowania składa się z następujących elementów:

- **Pakiet debugowania:** Debuger [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zapewnia ten sam interfejs użytkownika bez względu na to, co jest debugowane.

- **Menedżer debugowania sesji (SDM):** Zapewnia spójny interfejs programowy do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugera do zarządzania różnymi aparatami debugowania. Jest on realizowany [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]przez .

- **Menedżer debugowania procesów (PDM):** Zarządza, dla wszystkich uruchomionych [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]wystąpień , listę wszystkich programów, które mogą być lub są debugowane. Jest on realizowany [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]przez .

- **Aparat debugowania (DE):** Jest odpowiedzialny za monitorowanie debugowania programu, komunikowanie stanu uruchomionego programu do SDM i PDM oraz interakcję z ewaluatorem i dostawcą symboli w czasie rzeczywistym w celu zapewnienia analizy stanu pamięci i zmiennych programu w czasie rzeczywistym. Jest implementowany [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] przez (dla języków, które obsługuje) i dostawców innych firm, którzy chcą obsługiwać swój własny czas wykonywania.

- **Oceniający wyrażenie (EE):** Zapewnia obsługę dynamicznej oceny zmiennych i wyrażeń dostarczonych przez użytkownika, gdy program został zatrzymany w określonym punkcie. Jest implementowany [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] przez (dla języków, które obsługuje) i dostawców innych firm, którzy chcą obsługiwać własne języki.

- **Dostawca symboli (SP):** Nazywany również programem obsługi symboli, mapuje symbole debugowania programu na uruchomione wystąpienie programu, tak aby można było podać znaczące informacje (takie jak debugowanie na poziomie kodu źródłowego i ocena wyrażeń). Jest on implementowany przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (dla symboli wspólnego środowiska wykonawczego [CLR] i formatu pliku symbolu DataBase programu [PDB]) oraz przez dostawców innych firm, którzy mają własną zastrzeżoną metodę przechowywania informacji debugowania.

  Na poniższym diagramie przedstawiono relację między tymi elementami debugera programu Visual Studio.

  ![Omówienie składników debugowania](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")

## <a name="in-this-section"></a>W tej sekcji
 [Pakiet debugowania](../../extensibility/debugger/debug-package.md) W tym artykule omówiono pakiet [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowania, który działa w powłoce i obsługuje wszystkie interfejsu użytkownika.

 [Menedżer debugowania procesów](../../extensibility/debugger/process-debug-manager.md) Zawiera omówienie funkcji modułu PDM, który jest menedżerem procesów, które mogą być debugowane.

 [Menedżer debugowania sesji](../../extensibility/debugger/session-debug-manager.md) Definiuje SDM, który zapewnia ujednolicony widok sesji debugowania do IDE. SDM zarządza DE.

 [Aparat debugowania](../../extensibility/debugger/debug-engine.md) Dokumenty usługi debugowania, które zapewnia DE.

 [Tryby pracy](../../extensibility/debugger/operational-modes.md) Zawiera omówienie trzech trybów, w których IDE może działać: tryb projektowania, tryb uruchamiania i tryb przerwania. Omawiane są również mechanizmy przejściowe.

 [Ewaluator wyrażeń](../../extensibility/debugger/expression-evaluator.md) Wyjaśnia cel EE w czasie wykonywania.

 [Dostawca symboli](../../extensibility/debugger/symbol-provider.md) W tym artykule omówiono sposób, w jaki w implementacji dostawca symbolów ocenia zmienne i wyrażenia.

 [Wizualizator typu i przeglądarka niestandardowa](../../extensibility/debugger/type-visualizer-and-custom-viewer.md) W tym artykule omówiono, co wizualizator typu i niestandardowych viewer są i jaką rolę oceniający wyrażenie odgrywa we wspieraniu obu.

## <a name="related-sections"></a>Powiązane sekcje
 [Pojęcia debugera](../../extensibility/debugger/debugger-concepts.md) W tym artykule opisano główne debugowanie koncepcji architektury.

 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md) Wyjaśniono, jak DE działa jednocześnie w kontekście oceny kodu, dokumentacji i wyrażenia. Opisuje, dla każdego z trzech kontekstów, lokalizacji, pozycji lub oceny istotne dla niego.

 [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md) Zawiera łącza do różnych zadań debugowania, takich jak uruchamianie programu i oceny wyrażeń.

## <a name="see-also"></a>Zobacz też
- [Wprowadzenie](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
