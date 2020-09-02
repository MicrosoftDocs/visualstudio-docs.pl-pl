---
title: Przykłady Diagnostyka grafiki | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 45dd86b2-801e-4b07-a8c4-7bd25641d7f8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4df2fafb523d04a8ec222b10e1ac9ed3aa95454d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "73187932"
---
# <a name="graphics-diagnostics-examples"></a>Przykłady diagnostyki grafiki
W poniższych przykładach pokazano, jak debugować problemy z renderowaniem w aplikacjach opartych na technologii DirectX przy użyciu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Diagnostyka grafiki.

## <a name="capturing-graphics-information"></a>Przechwytywanie informacji graficznych
 Aby móc używać Diagnostyka grafiki do diagnozowania problemów z renderowaniem w aplikacji, musisz przechwycić informacje graficzne z aplikacji, gdy jest ona uruchomiona. Informacje o grafice mogą być przechwytywane z aplikacji, która jest uruchamiana lokalnie, lub z aplikacji uruchomionej na komputerze zdalnym lub innym urządzeniu. Te instruktaże pokazują, jak można ręcznie przechwycić informacje graficzne z aplikacji lub programowo:

- [Przewodnik: Przechwytywanie informacji graficznych](walkthrough-capturing-graphics-information.md)

- [Przewodnik: programowe przechwytywanie informacji graficznych](walkthrough-capturing-graphics-information-programmatically.md)

## <a name="use-graphics-diagnostics-with-an-arm-based-device"></a>Używanie Diagnostyka grafiki z urządzeniem ARM
 Możesz użyć Diagnostyka grafiki do debugowania aplikacji Direct3D na urządzeniu opartym na architekturze ARM przy użyciu zdalnego debugowania. Aby uzyskać więcej informacji [, zobacz jak: korzystanie z Diagnostyka grafiki z urządzeniem ARM](graphics-diagnostics-examples.md).

## <a name="playing-back-graphics-information"></a>Odtwarzanie informacji graficznych
 Po przechwyceniu informacji graficznych z działającej aplikacji można odtworzyć przechwycone zdarzenia, aby zdiagnozować problemy z renderowaniem. Aby odtworzyć, możesz użyć komputera deweloperskiego lub użyć komputera zdalnego lub urządzenia, z którym nawiązano połączenie. Aby uzyskać więcej informacji, zobacz [How to: Change a Diagnostyka grafiki playback Machine](how-to-change-the-graphics-diagnostics-playback-machine.md).

## <a name="debugging-missing-objects"></a>Debugowanie brakujących obiektów
 Brak obiektu (lub obiektów) to jeden z najczęstszych problemów z renderowaniem, które są używane przez deweloperów grafiki. Ten rodzaj problemu może być trudny do zdiagnozowania, ponieważ niektóre różne rodzaje błędów mogą spowodować zniknięcie obiektu. Typowe przyczyny braku obiektów obejmują błędnie skonfigurowany stan urządzenia, problemy związane z przekształcaniem geometrii obiektu lub nieprawidłowo skonfigurowany potok graficzny.

 Te scenariusze pokazują, jak można użyć Diagnostyka grafiki, aby określić przyczynę braku obiektu i znaleźć odpowiedni kod.

- [Przewodnik: brak obiektów spowodowany stanem urządzenia](walkthrough-missing-objects-due-to-device-state.md)

- [Przewodnik: brak obiektów spowodowany cieniowaniem wierzchołków](walkthrough-missing-objects-due-to-vertex-shading.md)

- [Przewodnik: brak obiektów spowodowany błędnie skonfigurowanym potokiem](walkthrough-missing-objects-due-to-misconfigured-pipeline.md)

## <a name="debugging-rendering-errors"></a>Debugowanie błędów renderowania
 Obiekt (lub obiekty) nie ma poprawnego wyglądu jest innym typowym problemem, który oferuje deweloperzy grafiki. Ten rodzaj problemu może być trudny do zdiagnozowania, ponieważ nieprawidłowy wygląd, a jego przyczyna — może być bardziej oczywisty — powiązanie niewłaściwej tekstury — jest to bardzo delikatne — usterka w kodzie programu do cieniowania lub nieoczekiwana interakcja między programami do cieniowania. Niektóre problemy mogą być spowodowane przez kombinację błędów.

 Poniżej przedstawiono scenariusz, w którym pokazano, jak można użyć Diagnostyka grafiki do śledzenia problemu z renderowaniem niesubtelnym, który jest spowodowany przez drobną usterkę programu do cieniowania:

- [Przewodnik: debugowanie błędów renderowania spowodowanych cieniowaniem](walkthrough-debugging-rendering-errors-due-to-shading.md)

## <a name="debugging-compute-shaders"></a>Debugowanie programów do cieniowania obliczeń
 Za pomocą Diagnostyka grafiki można debugować jądra DirectCompute obliczeń, które generują nieprawidłowe wyniki. Za pomocą DirectCompute można użyć obliczeniowej mocy procesora GPU do wykonywania obliczeń na dużej liczbie elementów danych równolegle. W przypadku niektórych rodzajów problemów użycie procesora GPU może wykonać wiele razy szybciej niż jeszcze bardziej zoptymalizowany kod procesora. Jednak tradycyjne debugery nie mogą wykryć kodu działającego na procesorze GPU. Debugowanie tego rodzaju kodu wymaga wyspecjalizowanych narzędzi, które są często specyficzne dla dostawcy i mogą nie być dobrze zintegrowane z programem Visual Studio. Aby debugowanie obliczeniowe programu do cieniowania w różnych procesorach GPU było bardziej spójne, Diagnostyka grafiki przechwytuje zdarzenia wysyłania DirectCompute (oprócz zdarzeń renderowania Direct3D), dzięki czemu można używać znanych narzędzi do debugowania problemów w kodzie programu do cieniowania.

 W przypadku scenariusza, w którym pokazano, jak debugować problem symulacji spowodowany usterką w cieniowaniu obliczeń, zobacz [Przewodnik: używanie Diagnostyka grafiki do debugowania cieniowania obliczeń](walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader.md).