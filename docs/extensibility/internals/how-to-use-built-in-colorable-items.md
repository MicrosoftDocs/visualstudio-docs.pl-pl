---
title: 'Instrukcje: korzystanie z Built-In elementów z możliwością kolorowania | Microsoft Docs'
description: Dowiedz się, jak używać wbudowanych elementów z możliwością kolorowania w zintegrowanym środowisku programistycznym (IDE) programu Visual Studio dla usługi językowej.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 253c108fe83eaf44f945f546bd64dd6529de1dd6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086082"
---
# <a name="how-to-use-built-in-colorable-items"></a>Instrukcje: korzystanie z wbudowanych elementów z możliwością kolorowania
Przed użyciem wbudowanych elementów, należy najpierw zasygnalizować zintegrowane środowisko programistyczne (IDE), które nie udostępniają własnych niestandardowych elementów, które w tym przypadku byłyby <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> obiektami. W tym celu należy ustawić wpis rejestru dla usługi językowej.

## <a name="to-use-built-in-colorable-items"></a>Aby używać wbudowanych elementów z możliwością kolorowania

1. W obszarze **HKEY_LOCAL_MACHINE\VisualStudio\\<X. Y> \languages\language Services \\<nazwa \> języka**, gdzie \<X.Y> jest wersją [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i \<Language Name> jest nazwą języka, utwórz wartość wpisu rejestru DWORD o nazwie **RequestStockColors**.

2. Ustaw wartość wpisu rejestru **RequestStockColors** na *1*.

    Po utworzeniu wpisu rejestru Metoda kolorowania <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> może użyć elementów członkowskich <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> wyliczenia, aby wypełnić tablicę atrybutów koloru używanych przez Edytor.

   > [!NOTE]
   > Nie ustawiaj tego wpisu rejestru, jeśli udostępniasz elementy niestandardowe. Aby uzyskać więcej informacji, zobacz [niestandardowe elementy do wykonania](../../extensibility/internals/custom-colorable-items.md).

## <a name="see-also"></a>Zobacz też
- [Kolorowanie składni w edytorach niestandardowych](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementowanie kolorowania składni](../../extensibility/internals/implementing-syntax-coloring.md)
- [Elementy niestandardowe z możliwością kolorowania](../../extensibility/internals/custom-colorable-items.md)
- [Rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service2.md)
