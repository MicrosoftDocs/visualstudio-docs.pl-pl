---
title: 'Jak: Użyj wbudowanych elementów colorable | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34e07894c3306f544396e53001990f7b9a2df5a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707787"
---
# <a name="how-to-use-built-in-colorable-items"></a>Jak: Używanie wbudowanych elementów kolorowych
Przed użyciem wbudowanych elementów colorable, należy najpierw sygnał do zintegrowanego środowiska programistycznego (IDE), że nie są <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> dostarczanie własnych niestandardowych elementów colorable, które w tym przypadku będą obiekty. Można to zrobić, ustawiając wpis rejestru dla usługi języka.

## <a name="to-use-built-in-colorable-items"></a>Aby użyć wbudowanych elementów kolorowych

1. W **obszarze HKEY_LOCAL_MACHINE\VisualStudio\\<X.Y>\Languages\Languages\Language\\ Services<Language\>Name** \<, gdzie X.Y> jest [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \<wersją i nazwą języka> jest nazwą języka, utwórz wartość wpisu rejestru DWORD o nazwie **RequestStockColors**.

2. Ustaw wartość wpisu rejestru **RequestStockColors** na *1*.

    Po utworzeniu wpisu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> rejestru, metoda colorizer może używać <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> członków wyliczenia, aby wypełnić tablicę atrybutów kolorów do użycia przez edytora.

   > [!NOTE]
   > Nie należy ustawiać tego wpisu rejestru, jeśli są dostarczanie niestandardowych elementów colorable. Aby uzyskać więcej informacji, zobacz [Niestandardowe elementy do barwienia](../../extensibility/internals/custom-colorable-items.md).

## <a name="see-also"></a>Zobacz też
- [Kolorowanie składni w edytorach niestandardowych](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Kolorowanie składni w starszej usłudze językowej](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementowanie kolorowania składni](../../extensibility/internals/implementing-syntax-coloring.md)
- [Niestandardowe elementy nadajne kolorami](../../extensibility/internals/custom-colorable-items.md)
- [Rejestrowanie starszej usługi językowej](../../extensibility/internals/registering-a-legacy-language-service2.md)
