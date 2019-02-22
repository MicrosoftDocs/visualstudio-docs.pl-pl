---
title: Omówienie kolorów i czcionek | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], font and color
- font and color control [Visual Studio SDK], editors
ms.assetid: 2203e4e7-8b7f-44ec-8884-6ff718d4f278
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da93d4f98bf3795c2dd60b02f9cf5b332b022ad2
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56684965"
---
# <a name="font-and-color-overview"></a>Omówienie czcionek i kolorów
W tym temacie omówiono ustawienia czcionek i kolorów tekstu w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zintegrowanego środowiska programistycznego (IDE). Wprowadza pojęcia związane z kategorii i wyświetlenie elementów i opisuje, jak pakietów VSPackage i podstawowy edytor za pomocą atrybutów tekstu.

## <a name="the-fonts-and-colors-property-page"></a>Czcionki i kolory właściwości strony
 Możesz zarządzać atrybutów tekstu wyświetlanego w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zintegrowanego środowiska programistycznego (IDE) za pośrednictwem **czcionki i kolory** stronę właściwości. Aby znaleźć **czcionki i kolory** na stronie właściwości **narzędzia** menu, kliknij przycisk **opcje**. Rozwiń **środowiska**, a następnie kliknij przycisk **czcionki i kolory**.

## <a name="categories-and-display-items"></a>Kategorie i wyświetlenie elementów
 Czcionki i kolory są pogrupowane w **kategorie** i **Wyświetle elementy**.

- A **kategorii** to kontener logiczny lub funkcjonalności szereg **Wyświetle elementy**.

   Lista **kategorie** znajduje się w **Pokaż ustawienia dla** pole listy rozwijanej **czcionki i kolory** stronę właściwości.

- A **wyświetlanego elementu** jest jednostką dobrze zdefiniowanych tekstu, takie jak komentarz, ciągu lub strukturę kontrolki, która jest pokolorowany, po wyświetleniu.

  Każdy **wyświetlanego elementu** unikatowo zdefiniowane **kategorii** zawierający go. W związku z tym, więcej niż jeden **kategorii** może mieć **wyświetlanego elementu** o takiej samej nazwie.

## <a name="vspackage-control-of-fonts-and-colors"></a>Pakietu VSPackage kontroli nad czcionki i kolory
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Umożliwia pakietów VSPackage do:

- Zdefiniuj czcionek i kolorów **kategorie**.

- Określ czcionek i kolorów używany do wyświetlania zawartości **Wyświetle elementy**.

- Interakcja z **czcionki i kolory** stronę właściwości.

- Wiele agregacji **kategorie** do grup.

- Utrwalanie zmian w domyślnych ustawieniach.

  Istnieją dwa sposoby interakcji z wyborów czcionek i kolorów w ramach [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)].

- Jednym ze sposobów jest określany jako *kolorowanie składni*. Jest on używany przez pakietu VSPackage, który dostosowuje istniejące [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] edytora do wdrożenia usługi językowej i tworzenia źródła edytora.

   Tylko jeden **kategorii** obsługuje ten mechanizm, to znaczy, **edytora tekstów**.

- Bardziej ogólnych zamiast obsługuje wszystkie inne **kategorie** i składników interfejsu użytkownika inne niż Edytor źródła, podczas wyświetlania tekstu. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>.

## <a name="core-editor-text-settings"></a>Ustawienia programu Core edytora tekstu
 Ustawienia czcionek i kolorów dla podstawowy Edytor obiektu usługi języka są regulowane przez **EditorCategory tekstu** w **Pokaż ustawienia dla** pole listy rozwijanej **czcionki i kolory** stronę właściwości.

 Podczas pracy z edytory, należy użyć czcionki wyspecjalizowanych i mechanizmu kontroli kolorów, zapewniającej usługa językowa kontroli i rozszerzanie **edytora tekstów** ustawienia. Ten mechanizm jest określany jako *kolorowanie składni* oraz zapewnia:

- Uproszczona metoda zarządzania czcionki i kolory wyświetle elementy.

   Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.

- Mechanizm kolorowanie dobrze zdefiniowane i zoptymalizowane.

   Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>.

- Możliwość zarówno Użyj wbudowanych wyświetle elementy z **EditorCategory tekst** i rozszerzyć je.

   Aby uzyskać więcej informacji, zobacz [jak: Używanie wbudowanych elementów z możliwością kolorowania](../extensibility/internals/how-to-use-built-in-colorable-items.md) i [niestandardowe elementy z możliwością kolorowania](../extensibility/internals/custom-colorable-items.md).

- Automatyczne trwałości bieżącego stanu obu wbudowanych i niestandardowych wyświetlania elementów z **edytora tekstów** kategorii.

  Aby uzyskać więcej informacji, zobacz kolorowania składni [kolorowanie składni w starszej wersji usługi językowej](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).

## <a name="see-also"></a>Zobacz także
- [Interfejsy starszej wersji w edytorze](../extensibility/legacy-interfaces-in-the-editor.md)
- [Kolorowanie składni w starszej wersji usługi językowej](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)