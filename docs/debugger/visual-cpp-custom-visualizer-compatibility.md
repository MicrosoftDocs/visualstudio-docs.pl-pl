---
title: Zgodność wizualizacjiC++ języka Visual C/niestandardowego
ms.date: 01/28/2019
ms.prod: visual-studio-dev16
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging assertions
- assertions, debugging
- assertions, assertion failures
- Assertion Failed dialog box
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: 9fdd44be89fde2fbc26038c8b88fff405876264f
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72430620"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Zgodność wizualizacjiC++ języka Visual C/niestandardowego

Począwszy od programu Visual Studio 2019 C++ , program zawiera udoskonalony debuger, który używa zewnętrznego procesu 64-bitowego do hostowania składników intensywnie korzystających z pamięci. W ramach tej aktualizacji Niektóre rozszerzenia ewaluatora C/C++ Expression muszą zostać zaktualizowane, aby były zgodne z nowym debugerem.

Jeśli obecnie korzystasz z starszego dodatku C/C++ EE lub wizualizacji językaC++ c/niestandardowego, możesz wyłączyć korzystanie z tego procesu zewnętrznego, przechodząc do opcji **narzędzia** > **Opcje** > **debugowania**, a następnie anulując wybór **debugowania ładowania symbole w procesie zewnętrznym (tylko kod natywny)** . Jeśli ta opcja zostanie odprowadzona, wystąpi znaczący wzrost użycia pamięci w procesie IDE (devenv. exe). Dlatego, jeśli oczekujesz na Debugowanie dużych projektów, zaleca się współdziałanie z właścicielem rozszerzenia, aby była zgodna z tą opcją debugowania.

Jeśli jesteś właścicielem starszego dodatku C/C++ EE lub wizualizacji c/C++ Custom, możesz znaleźć więcej informacji na temat rezygnacji z załadowania rozszerzenia w procesie roboczym na [przykładach rozszerzalności Concord](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting). Możesz również znaleźć [przykład C/C++ Custom wizualizatora](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer).