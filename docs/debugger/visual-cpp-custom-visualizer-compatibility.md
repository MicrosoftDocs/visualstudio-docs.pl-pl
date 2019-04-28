---
title: Zgodność niestandardowego wizualizatora Visual C/C++
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
ms.openlocfilehash: 32e38dd3bba8a1127d8756972b73e8b47a514f1b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62901169"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Zgodność niestandardowego wizualizatora Visual C/C++

Począwszy od programu Visual Studio 2019 Visual C++ obejmuje ulepszone debugera, który używa zewnętrznego procesu 64-bitowego do hostowania jej składniki wymagających dużej ilości pamięci. W ramach tej aktualizacji należy zaktualizować niektórych rozszerzeń Ewaluator wyrażeń Visual C/C++, aby były zgodne z debugerem nowe.

Jeśli aktualnie używanym starszej wersji dodatku EE C/C++ lub C/C++ niestandardowego wizualizatora, można wyłączyć użycia to proces zewnętrzny, przechodząc do **narzędzia** > **opcje**  >   **Debugowanie**, a następnie usunięcie zaznaczenia tej opcji **debugowania ładowania symboli w procesie zewnętrznym (tylko natywne)**. Jeśli wyłączysz tę opcję, wystąpią znaczne zwiększenie użycia pamięci w ramach procesu IDE (devenv.exe). Tak Jeśli spodziewasz się debugowania dużych projektów, zalecane jest, należy skontaktować się z właścicielem rozszerzenia, aby był zgodny z tą opcją debugowania.

Jeśli jesteś właścicielem starszej wersji dodatku EE C/C++ lub C/C++ niestandardowego wizualizatora, można znaleźć więcej informacji na temat ładowania rozszerzenia w procesie roboczym na włączenie [rozszerzalności Concord przykłady wiki](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting). Możesz również znaleźć [przykładowe niestandardowego wizualizatora C/C++](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer).