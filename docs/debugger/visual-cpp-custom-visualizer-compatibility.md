---
title: Zgodność niestandardowego wizualizatora Visual C/C++
ms.date: 01/28/2019
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging assertions
- assertions, debugging
- assertions, assertion failures
- Assertion Failed dialog box
ms.assetid: 64af5bed-e38b-420f-b9ce-d64f35100aae
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: 3c90c66e338330d77af29564c7586e68b8ee35b6
ms.sourcegitcommit: 01334abf36d7e0774329050d34b3a819979c95a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55852611"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Zgodność niestandardowego wizualizatora Visual C/C++

Począwszy od programu Visual Studio 2019 Visual C++ obejmuje ulepszone debugera, który używa zewnętrznego procesu 64-bitowego do hostowania jej składniki wymagających dużej ilości pamięci. W ramach tej aktualizacji należy zaktualizować niektórych rozszerzeń Ewaluator wyrażeń Visual C/C++, aby były zgodne z debugerem nowe.

Jeśli aktualnie używanym starszej wersji dodatku EE C/C++ lub C/C++ niestandardowego wizualizatora, można wyłączyć użycia to proces zewnętrzny, przechodząc do **narzędzia** > **opcje**  >   **Debugowanie**, a następnie usunięcie zaznaczenia tej opcji **debugowania ładowania symboli w procesie zewnętrznym (tylko natywne)**. Jeśli wyłączysz tę opcję, wystąpią znaczne zwiększenie użycia pamięci w ramach procesu IDE (devenv.exe). Tak Jeśli spodziewasz się debugowania dużych projektów, zalecane jest, należy skontaktować się z właścicielem rozszerzenia, aby był zgodny z tą opcją debugowania.

Jeśli jesteś właścicielem starszej wersji dodatku EE C/C++ lub C/C++ niestandardowego wizualizatora, można znaleźć więcej informacji na temat ładowania rozszerzenia w procesie roboczym na włączenie [rozszerzalności Concord przykłady wiki](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting). Możesz również znaleźć [przykładowe niestandardowego wizualizatora C/C++](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer).