---
title: Przykłady diagnostyki grafiki | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 45dd86b2-801e-4b07-a8c4-7bd25641d7f8
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 52c1c2cc7304828e9ace7e9b5072d262a5395a1d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54774985"
---
# <a name="graphics-diagnostics-examples"></a>Przykłady diagnostyki grafiki
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Te przykłady przedstawiają sposób debugowania problemów z renderowaniem w aplikacjach opartych na technologii DirectX przy użyciu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] diagnostyki grafiki.  
  
## <a name="capturing-graphics-information"></a>Przechwytywanie informacji graficznych  
 Zanim użyjesz diagnostyki grafiki do diagnozowania problemów z renderowaniem w aplikacji należy przechwytywać informacje graficzne z aplikacji, gdy jest on uruchomiony. Można przechwycić informacje graficzne z aplikacji, która jest uruchomiona lokalnie lub aplikację, która jest uruchomiona na komputerze zdalnym lub innych urządzeń. Te przewodniki pokazują, jak ręcznie lub programowo, można przechwytywać informacje graficzne z aplikacji:  
  
-   [Przewodnik: Przechwytywanie informacji graficznych](../debugger/walkthrough-capturing-graphics-information.md)  
  
-   [Przewodnik: Programowe przechwytywanie informacji graficznych](../debugger/walkthrough-capturing-graphics-information-programmatically.md)  
  
## <a name="use-graphics-diagnostics-with-an-arm-based-device"></a>Diagnostyka grafiki za pomocą urządzenia z systemem ARM  
 Za pomocą Graphics Diagnostics do debugowania aplikacji Direct3D na urządzeniu z systemem ARM przy użyciu zdalnego debugowania. Aby uzyskać więcej informacji, zobacz [jak: Korzystanie z diagnostyki grafiki z urządzeniem ARM](../debugger/how-to-use-graphics-diagnostics-with-an-arm-device.md).  
  
## <a name="playing-back-graphics-information"></a>Odtwarzania informacji graficznych  
 Po przechwyceniu informacje graficzne z uruchomionej aplikacji, można odtwarzać przechwytywanych zdarzeń do diagnozowania problemów z renderowaniem. Do odtwarzania, możesz używać komputera deweloperskiego lub można użyć komputera zdalnego lub urządzenia, które są podłączone do. Aby uzyskać więcej informacji, zobacz [jak: Zmiana maszyny odtwarzania diagnostyki grafiki](../debugger/how-to-change-the-graphics-diagnostics-playback-machine.md).  
  
## <a name="debugging-missing-objects"></a>Debugowanie brakujących obiektów  
 Brak obiektu (lub obiektów) jest jednym z najbardziej typowe problemy z renderowaniem środowisko deweloperów grafiki. Tego rodzaju problem może być trudne do zdiagnozowania, ponieważ wiele rodzajów błędów może spowodować, że obiekt, do najwyraźniej zniknąć. Typowe przyczyny występowania brakujących obiektów obejmują stan urządzenia nieprawidłowo, problemy z Przekształcanie obiektu, który lub potoku grafiki nieprawidłowo skonfigurowane.  
  
 Te scenariusze pokazują, jak można użyć diagnostyki grafiki, aby ustalić, dlaczego brakuje obiektu i znaleźć kod, który jest odpowiedzialny.  
  
-   [Przewodnik: Brak obiektów spowodowany stanem urządzenia](../debugger/walkthrough-missing-objects-due-to-device-state.md)  
  
-   [Przewodnik: Brak obiektów spowodowany cieniowaniem wierzchołków](../debugger/walkthrough-missing-objects-due-to-vertex-shading.md)  
  
-   [Przewodnik: Brak obiektów spowodowany błędnie skonfigurowanym potokiem](../debugger/walkthrough-missing-objects-due-to-misconfigured-pipeline.md)  
  
## <a name="debugging-rendering-errors"></a>Debugowanie błędów renderowania  
 Obiekt (lub obiektów), nie ma poprawne wygląd jest inny problem wspólnej, który deweloperzy grafiki doświadczeniem. Tego rodzaju problemy mogą być trudne do zdiagnozowania, ponieważ niepoprawne wygląd, a jego przyczyny, należą do zakresu od bardzo oczywiste — powiązania niewłaściwego tekstury — do bardzo subtelne — usterki w kodzie programu do cieniowania lub nieoczekiwany interakcji między programów do cieniowania. Niektórych problemów może być spowodowany przez kombinację błędy.  
  
 Poniżej przedstawiono scenariusz, w którym pokazano, jak można użyć diagnostyki grafiki do śledzenia problemu z renderowaniem nie tak subtelne, który jest powodowany przez usterkę pomocnicza programu do cieniowania:  
  
-   [Przewodnik: Debugowanie błędów renderowania spowodowanych cieniowaniem](../debugger/walkthrough-debugging-rendering-errors-due-to-shading.md)  
  
## <a name="debugging-compute-shaders"></a>Debugowania obliczających programów cieniujących  
 Za pomocą Graphics Diagnostics do debugowania jądra cieniowania obliczenia DirectCompute, generujących niepoprawne wyniki. Za pomocą DirectCompute moc obliczeniową procesora GPU służy do wykonywania obliczeń na dużą liczbę elementów danych w sposób równoległy. Dla niektórych rodzajów problemów, przy użyciu procesora GPU mogą wykonywać wiele razy szybciej niż nawet dobrze zoptymalizowanego kodu procesora CPU. Jednak tradycyjne debugerów nie może wykryć kodu, który działa na procesorze GPU. Debugowanie tego rodzaju kod wymaga specjalistycznych narzędzi, które często są specyficzne dla dostawcy, a nie może być zintegrowana z dobrze z programem Visual Studio. Aby debugowania cieniowania obliczenia spójniejsze w zakresie GPU, diagnostyki grafiki przechwytuje zdarzenia wysyłki DirectCompute — oprócz zdarzeń renderowania Direct3D — dzięki czemu można użyć znanych narzędzi do debugowania problemów w kodzie cieniowania obliczenia.  
  
 Scenariusz, który demonstruje, jak można debugować problem symulacji, który jest powodowany przez usterkę w cieniowania obliczenia można znaleźć [instruktażu: Używanie Graphics Diagnostics do debugowania cieniowania obliczenia](../debugger/walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader.md).
