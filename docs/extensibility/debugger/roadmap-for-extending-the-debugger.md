---
title: Plan rozszerzenia debugera | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e809eeb6a1a5d2c24368932713d69c7199b5af38
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713145"
---
# <a name="roadmap-for-extending-the-debugger"></a>Plan rozszerzenia debugera
Ta dokumentacja zawiera przewodnik i [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] informacje referencyjne [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]dotyczące rozszerzania debugera za pomocą pliku .

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]debugowanie dokumentacji zawiera przykłady, wyczerpujące odwołanie i kilka reprezentatywnych scenariuszy, które pokazują typowe sposoby dostosowania debugera.

 Kompilator i jego dane wyjściowe określają, co jest wymagane do skonfigurowania debugowania w produkcie. Jeśli kompilator:

- Jest przeznaczony dla natywnego systemu operacyjnego Windows i zapisuje *plik . PDB,* można debugować programy za pomocą natywnego aparatu debugowania kodu (DE), który jest zintegrowany z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Nie trzeba implementować DE lub oceniający wyrażenie. Oceniający wyrażenie jest zapisywany dla składni języka programowania C++.

- Produkuje dane wyjściowe języka pośredniego firmy Microsoft (MSIL), można debugować programy za [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]pomocą zarządzanego aparatu debugowania kodu DE, który jest również zintegrowany z programem . W związku z tym wystarczy tylko zaimplementować oceniającego wyrażenie. Przykładowy ewaluator wyrażenia jest dla Ciebie. Aby uzyskać więcej informacji, zobacz następujące tematy:

   [Ocena wyrażenia](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)

   [Ocena wyrażeń](../../extensibility/debugger/evaluating-expressions.md)

   [Kontekst oceny wyrażenia](../../extensibility/debugger/expression-evaluation-context.md)

   [Ocena wyrażenia w trybie przerwania](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

   [Pisanie ewaluatora wyrażeń środowiska uruchomieniowego języka wspólnego](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

- Jest przeznaczony dla zastrzeżonego systemu operacyjnego lub innego środowiska w czasie wykonywania, musisz napisać własne DE. Dostępny jest samouczek, który tworzy prosty DE przy użyciu ATL COM. Aby uzyskać więcej informacji, zobacz następujące tematy:

   [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md)

   [Samouczek: Tworzenie aparatu debugowania przy użyciu ATL COM](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)

   [Wdrażanie dostawcy portu](../../extensibility/debugger/implementing-a-port-supplier.md)

   [Samples](../../extensibility/debugger/visual-studio-debugging-samples.md)

## <a name="see-also"></a>Zobacz też
- [Wprowadzenie](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
