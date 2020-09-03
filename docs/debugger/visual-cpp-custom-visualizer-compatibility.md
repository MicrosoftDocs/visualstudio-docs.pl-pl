---
title: Zgodność niestandardowego wizualizatora języka Visual C/C++
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72430620"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Zgodność niestandardowego wizualizatora języka Visual C/C++

Począwszy od programu Visual Studio 2019, C++ zawiera udoskonalony debuger, który używa zewnętrznego procesu 64-bitowego do hostowania składników intensywnie korzystających z pamięci. W ramach tej aktualizacji Niektóre rozszerzenia ewaluatora wyrażeń C/C++ muszą zostać zaktualizowane, aby były zgodne z nowym debugerem.

Jeśli obecnie korzystasz ze starszej wersji dodatku c/c++ EE lub niestandardowego wizualizatora c/c++, możesz wyłączyć użycie tego procesu zewnętrznego, przechodząc do opcji **Narzędzia**  >  **Options**  >  **debugowania**, a następnie usunąć zaznaczenie **symboli debugowania ładowania w procesie zewnętrznym (tylko kod natywny)**. Jeśli ta opcja zostanie odprowadzona, wystąpi znaczący wzrost użycia pamięci w procesie IDE (devenv.exe). Dlatego, jeśli oczekujesz na Debugowanie dużych projektów, zaleca się współdziałanie z właścicielem rozszerzenia, aby była zgodna z tą opcją debugowania.

Jeśli jesteś właścicielem starszej wersji dodatku C/C++ EE lub niestandardowego wizualizatora C/C++, możesz znaleźć więcej informacji na temat rezygnacji z załadowania rozszerzenia w procesie roboczym na [przykładach rozszerzalności Concord](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting). Możesz również znaleźć [przykład niestandardowego wizualizatora C/C++](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer).