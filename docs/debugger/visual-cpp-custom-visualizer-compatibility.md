---
title: Zgodność niestandardowego wizualizatora języka Visual C/C++
description: Nowa funkcja w programie Visual Studio 2019 może nie być zgodna ze starszymi dodatkami ewaluatora wyrażeń C/C++ i wizualizacjami niestandardowymi. Zobacz ten artykuł, aby uzyskać szczegółowe informacje.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: dea92f6aad54b8c75c43a1078142595e17fa2ef6
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149797"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Zgodność niestandardowego wizualizatora języka Visual C/C++

Począwszy od programu Visual Studio 2019, C++ zawiera udoskonalony debuger, który używa zewnętrznego procesu 64-bitowego do hostowania składników intensywnie korzystających z pamięci. W ramach tej aktualizacji Niektóre rozszerzenia ewaluatora wyrażeń C/C++ muszą zostać zaktualizowane, aby były zgodne z nowym debugerem.

Jeśli obecnie korzystasz z starszego niestandardowego wizualizatora c/c++ lub w języku c/c++, możesz wyłączyć użycie tego procesu zewnętrznego, przechodząc do opcji **Narzędzia**  >    >  **debugowania**, a następnie usuwając zaznaczenie **symboli debugowania ładowania w procesie zewnętrznym (tylko kod natywny)**. Jeśli ta opcja zostanie odprowadzona, wystąpi znaczący wzrost użycia pamięci w procesie IDE (devenv.exe). Dlatego, jeśli oczekujesz na Debugowanie dużych projektów, zaleca się współdziałanie z właścicielem rozszerzenia, aby była zgodna z tą opcją debugowania.

Jeśli jesteś właścicielem starszego niestandardowego wizualizatora C/C++ lub dodatku C/C++, możesz znaleźć więcej informacji na temat rezygnacji z ładowania rozszerzenia w procesie roboczym na [przykładach rozszerzalności Concord](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting). Możesz również znaleźć [przykład niestandardowego wizualizatora C/C++](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer).