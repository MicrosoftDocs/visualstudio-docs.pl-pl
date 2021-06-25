---
title: Składniki debugera | Microsoft Docs
description: Dowiedz się więcej o elementach, które są sesją debugowania, która jest zarządzana przez debuger Visual Studio wdrożony jako pakiet VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8c246bc00ee4f6fcead8404b3174da39f7b5ca2d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903986"
---
# <a name="debugger-components"></a>Składniki debugera
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Debuger jest implementowana jako pakiet VSPackage i zarządza całą sesją debugowania. Sesja debugowania składa się z następujących elementów:

- **Pakiet debugowania:** Debuger [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] udostępnia ten sam interfejs użytkownika niezależnie od tego, co jest debugowane.

- **Menedżer debugowania sesji (SDM):** Zapewnia spójny interfejs programowy debugera do zarządzania różnymi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aparatami debugowania. Jest on implementowany [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] przez .

- **Menedżer debugowania procesów (PDM):** Zarządza dla wszystkich uruchomionych wystąpień programu listą wszystkich programów, które mogą być lub [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] są debugowane. Jest on implementowany [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] przez .

- **Aparat debugowania (DE):** Odpowiada za monitorowanie debugowanych programów, przekazywanie informacji o stanie uruchomionego programu do programu SDM i pdm oraz interakcję z ewaluatorem wyrażeń i dostawcą symboli w celu zapewnienia analizy stanu pamięci i zmiennych programu w czasie rzeczywistym. Jest on implementowany przez (w przypadku języków, które obsługuje) i innych dostawców, którzy chcą obsługiwać [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] własny czas działania.

- **Ewaluator wyrażeń (EE):** Zapewnia obsługę dynamicznego oceniania zmiennych i wyrażeń dostarczonych przez użytkownika, gdy program został zatrzymany w określonym punkcie. Jest on implementowany przez (w przypadku języków, które obsługuje) i innych dostawców, którzy chcą obsługiwać [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] własne języki.

- **Dostawca symboli:** Nazywany również programem obsługi symboli mapuje symbole debugowania programu na uruchomione wystąpienie programu, aby można było uzyskać istotne informacje (takie jak debugowanie na poziomie kodu źródłowego i ocena wyrażeń). Jest implementowany przez program (dla symboli środowiska uruchomieniowego języka wspólnego [CLR] i format pliku symboli DataBase programu [PDB]) oraz przez innych dostawców, którzy mają własną zastrzeżoną metodę przechowywania informacji [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowania.

  Na poniższym diagramie przedstawiono relację między tymi elementami Visual Studio debugowania.

  ![Omówienie składników debugowania](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")

## <a name="in-this-section"></a>W tej sekcji
 [Pakiet debugowania](../../extensibility/debugger/debug-package.md) W tym artykule omówiono pakiet debugowania, który jest uruchamiany w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] powłoki i obsługuje cały interfejs użytkownika.

 [Menedżer debugowania procesów](../../extensibility/debugger/process-debug-manager.md) Zawiera omówienie funkcji pdm, który jest menedżerem procesów, które można debugować.

 [Menedżer debugowania sesji](../../extensibility/debugger/session-debug-manager.md) Definiuje SDM, który zapewnia ujednolicony widok sesji debugowania środowiska IDE. SdM zarządza DE.

 [Aparat debugowania](../../extensibility/debugger/debug-engine.md) Dokumentuje usługi debugowania, które de zapewnia.

 [Tryby operacyjne](../../extensibility/debugger/operational-modes.md) Zawiera omówienie trzech trybów, w których może działać środowiska IDE: tryb projektowania, tryb uruchamiania i tryb przerwania. Omówiono również mechanizmy przejścia.

 [Ewaluator wyrażeń](../../extensibility/debugger/expression-evaluator.md) Wyjaśnia cel EE w czasie rzeczywistym.

 [Dostawca symboli](../../extensibility/debugger/symbol-provider.md) W tym artykule omówiono, jak podczas implementacji dostawca symboli ocenia zmienne i wyrażenia.

 [Wizualizator typów i przeglądarka niestandardowa](../../extensibility/debugger/type-visualizer-and-custom-viewer.md) Omówienie wizualizatora typów i przeglądarki niestandardowej oraz roli, jaką odgrywa ewaluator wyrażeń w wspieraniu obu typów.

## <a name="related-sections"></a>Powiązane sekcje
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md) Opisuje główne pojęcia dotyczące architektury debugowania.

 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md) Wyjaśnia, jak de działa jednocześnie w kodzie, dokumentacji i kontekstach oceny wyrażeń. Opisuje dla każdego z trzech kontekstów odpowiednią lokalizację, pozycję lub ocenę.

 [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md) Zawiera linki do różnych zadań debugowania, takich jak uruchamianie programu i ocenianie wyrażeń.

## <a name="see-also"></a>Zobacz też
- [Wprowadzenie](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
