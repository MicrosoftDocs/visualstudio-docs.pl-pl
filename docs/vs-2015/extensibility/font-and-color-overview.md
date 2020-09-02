---
title: Przegląd czcionek i kolorów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], font and color
- font and color control [Visual Studio SDK], editors
ms.assetid: 2203e4e7-8b7f-44ec-8884-6ff718d4f278
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0a20cfa2372b1e55652ffcebe6d173cff86140a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204346"
---
# <a name="font-and-color-overview"></a>Omówienie czcionek i kolorów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie omówiono ustawienia czcionek i kolorów tekstu w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zintegrowanym środowisku programistycznym (IDE). Wprowadza również pojęcia dotyczące kategorii i elementów wyświetlanych i opisuje sposób, w jaki pakietów VSPackage i podstawowy edytor używają atrybutów tekstu.  
  
## <a name="the-fonts-and-colors-property-page"></a>Strona właściwości czcionki i kolory  
 Można zarządzać atrybutami wyświetlanego tekstu w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zintegrowanym środowisku programistycznym (IDE) za pomocą strony właściwości **czcionki i kolory** . Aby znaleźć stronę właściwości **czcionki i kolory** , w menu **Narzędzia** kliknij polecenie **Opcje**. Rozwiń węzeł **środowisko**, a następnie kliknij pozycję **czcionki i kolory**.  
  
## <a name="categories-and-display-items"></a>Kategorie i elementy wyświetlania  
 Czcionki i kolory są zorganizowane w **Kategorie** i **elementy wyświetlania**.  
  
- **Kategoria** jest kontenerem logicznym lub funkcjonalnym dla wielu **elementów wyświetlanych**.  
  
   Lista **kategorii** znajduje się w polu listy rozwijanej **Pokaż ustawienia dla** właściwości **czcionki i kolory** .  
  
- **Element wyświetlany** jest dobrze zdefiniowaną jednostką tekstową, taką jak komentarz, ciąg lub struktura kontrolki, która ma być wyświetlana w kolorze.  
  
  Każdy **element wyświetlany** jest jednoznacznie zdefiniowany w **kategorii** , która ją zawiera. W związku z tym więcej niż jedna **Kategoria** może mieć **element wyświetlany** o tej samej nazwie.  
  
## <a name="vspackage-control-of-fonts-and-colors"></a>Pakietu VSPackage kontrolę nad czcionkami i kolorami  
 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]Umożliwia pakietów VSPackage:  
  
- Definiowanie **kategorii**czcionek i kolorów.  
  
- Określ czcionki i kolory używane do prezentowania **elementów wyświetlanych**.  
  
- Korzystając ze strony właściwości **czcionki i kolory** .  
  
- Agreguj wiele **kategorii** do grup.  
  
- Utrwalaj zmiany w ustawieniach domyślnych.  
  
  Istnieją dwa sposoby współpracy z opcjami wyboru czcionek i kolorów w obrębie [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] .  
  
- Jeden ze sposobów jest określany jako *kolorowanie składni*. Jest on używany przez pakietu VSPackage, który dostosowuje istniejący [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Edytor do implementowania usługi językowej i tworzenia edytora źródła.  
  
   Tylko jedna **Kategoria** obsługuje ten mechanizm, a mianowicie **Edytor tekstu**.  
  
- Bardziej ogólna alternatywa obsługuje wszystkie inne **Kategorie** i składniki interfejsu użytkownika inne niż Edytor źródła podczas wyświetlania tekstu. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>.  
  
## <a name="core-editor-text-settings"></a>Ustawienia tekstu w edytorze podstawowym  
 Ustawienia czcionek i kolorów dla podstawowego edytora obiektu usługi językowej podlegają **EditorCategory tekstu** znalezionemu w polu listy rozwijanej **Pokaż ustawienia dla** strony właściwości **czcionki i kolory** .  
  
 Podczas pracy z edytorami należy używać wyspecjalizowanego mechanizmu kontroli czcionek i kolorów, który zapewnia usługa języka, aby kontrolować i zwiększać ustawienia **edytora tekstu** . Mechanizm jest określany jako *kolorowanie składni* i zapewnia:  
  
- Uproszczona technika zarządzania czcionkami i kolorami elementów wyświetlanych.  
  
   Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.  
  
- Dobrze zdefiniowany i zoptymalizowany mechanizm kolorowania.  
  
   Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>.  
  
- Możliwość użycia wbudowanych elementów wyświetlanych z **EditorCategory tekstu** i ich rozszerania.  
  
   Aby uzyskać więcej informacji, zobacz [jak: używać wbudowanych elementów](../extensibility/internals/how-to-use-built-in-colorable-items.md) i elementów [niestandardowych](../extensibility/internals/custom-colorable-items.md).  
  
- Automatyczna trwałość bieżącego stanu obu wbudowanych i niestandardowych elementów wyświetlanych z kategorią **Edytor tekstu** .  
  
  Aby uzyskać więcej informacji na temat kolorowania składni [, zobacz kolorowanie składni w starszej wersji usługi językowej](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Starsze interfejsy w edytorze](../extensibility/legacy-interfaces-in-the-editor.md)   
 [Kolorowanie składni w starszej wersji usługi językowej](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
