---
title: Stan pakietu VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- state, VSPackages
- VSPackages, managing application state
- state persistence
ms.assetid: 6056a9ea-e7a8-481c-9fc8-340229fa12d9
caps.latest.revision: 25
manager: jillfra
ms.openlocfilehash: f3140b527673f87b1d7c552e99584232494aed7f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62979998"
---
# <a name="vspackage-state"></a>Stan pakietu VSPackage
Wiele czynników określa zbiór wartości utrwalonych lub stanu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aplikacji.  
  
- Projekty mają właściwości projektu i konfiguracji.  
  
- Rozwiązania mają właściwości.  
  
- Ustawienia użytkownika określają rozmiar i położenie okien dokumentów, okien narzędzi, stanu dokowania i skrótów klawiaturowych.  
  
- Aplikacje mogą mieć opcje ustawiane przez użytkownika.  
  
- Obiekty tworzone przez aplikację mogą mieć własne właściwości.  
  
  Oto kilka sposobów [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zarządzania stanem aplikacji:  
  
- Za pomocą stron właściwości projektu i rozwiązania.  
  
- Za pomocą **Kreatora importowania i eksportowania ustawień**, który umożliwia użytkownikowi przenoszenie ustawień z jednego komputera do drugiego.  
  
- Za pomocą okna dialogowego **Opcje** , które zawiera opcje związane z aplikacjami.  
  
- Za pomocą okna **Właściwości** , które uwidacznia właściwości obiektów.  
  
- Za poorednictwem automatyzacji. Aplikacja może uzyskiwać dostęp do pakietu VSPackage i właściwości obiektów, które zostały uwidocznione w usłudze Automation.  
  
  Podstawowym stanem aplikacji są różne mechanizmy trwałości, które umożliwiają zapisanie i przywrócenie stanu aplikacji.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Obsługa trwałości stanu](../misc/support-for-state-persistence.md)  
 Wyświetla listę typowych strategii zapisywania, przywracania i resetowania stanu pakietu VSPackage.  
  
 [Opcje i strony opcji](../extensibility/internals/options-and-options-pages.md)  
 Wprowadza ogólne i niestandardowe strony opcji oraz wyjaśnia, jak je wdrożyć.  
  
 [Tworzenie strony opcji](../extensibility/creating-an-options-page.md)  
 Wyjaśnia, jak utworzyć dwie strony opcji, prostą stronę i stronę niestandardową.  
  
 [Obsługa kategorii ustawień](../misc/support-for-settings-categories.md)  
 Omawia ustawienia użytkownika oraz sposób ich tworzenia i utrwalania.  
  
 [Tworzenie kategorii ustawień](../extensibility/creating-a-settings-category.md)  
 Wyjaśnia, jak utworzyć [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kategorię ustawień i użyć jej do zapisania wartości i przywrócenia wartości z pliku ustawień.  
  
 [Rozszerzanie właściwości i okno właściwości](../extensibility/extending-properties-and-the-property-window.md)  
 Wyjaśnia, jak wyświetlić i zmienić wartość obiektu w oknie **Właściwości** .  
  
 [Uwidacznianie właściwości w oknie właściwości](../extensibility/exposing-properties-to-the-properties-window.md)  
 Wyjaśnia, jak uwidocznić właściwości publiczne obiektu do okna **Właściwości** .  
  
 [Pomoc techniczna dotycząca właściwości projektu i konfiguracji](../extensibility/internals/support-for-project-and-configuration-properties.md)  
 Wyjaśnia, jak wyświetlać i zmieniać właściwości projektu i konfiguracji.  
  
 [Pobieranie właściwości projektu](../extensibility/getting-project-properties.md)  
 Przeprowadzi Cię przez kroki tworzenia zarządzanego pakietu VSPackage, które wyświetla właściwości projektu w oknie narzędzi.  
  
 [Korzystanie z magazynu ustawień](../extensibility/using-the-settings-store.md)  
 Wyjaśnia ustawienia mechanizmu trwałości magazynu i sposobu jego użycia.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Pakiety VSPackage](../extensibility/internals/vspackages.md)  
 Zawiera ogólne wskazówki dotyczące sposobu tworzenia i używania pakietów VSPackage.