---
title: Kreatorzy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6e58ebd736f7bb9f35df6e41d5235f36f7037259
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687628"
---
# <a name="wizards"></a>Kreatory
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Po utworzeniu kreatora zazwyczaj należy dodać go do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zintegrowanego środowiska programistycznego (IDE), aby inne osoby mogły z niego korzystać. Dodany Kreator zostanie wyświetlony w oknach dialogowych **Dodaj nowy projekt** lub **Dodaj nowy element** . Aby wyświetlić okna dialogowe **Dodaj nowy projekt** lub **Dodaj nowy element** , kliknij prawym przyciskiem myszy otwarte rozwiązanie w **Eksplorator rozwiązań**, wskaż polecenie **Dodaj**, a następnie kliknij przycisk **Nowy projekt** lub **nowy element**.  
  
 Kreatory mogą być zaimplementowane w programie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , aby umożliwić użytkownikom wybranie z widoku drzewa dostępnych wartości po otwarciu okna dialogowego **Dodaj nowy projekt** lub okno dialogowe **Dodaj nowy element** lub po kliknięciu prawym przyciskiem myszy elementu w **Eksplorator rozwiązań**.  
  
 W kreatorze można podać opcję lokalizowania nazwy nowego projektu lub ITES. można także określić ikonę, która będzie widoczna dla użytkowników podczas wybierania kreatora. Można również kontrolować kolejność wyświetlania nowych elementów względem innych dostępnych elementów. elementy nie muszą być zorganizowane alfabetycznie.  
  
 Możesz również podać kreatora, który jest uruchamiany inaczej, na podstawie parametrów niestandardowych, które są przenoszone do kreatora, gdy zostanie on otwarty.  
  
 W tematach w tej sekcji omówiono zaimplementowane pliki, które powodują wyświetlenie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] okien dialogowych **Dodaj nowy projekt** i **Dodaj nowy element** , aby wyświetlić listę kreatorów spośród dostępnych kreatorów i szablonów oraz wymagania, które Kreator musi spełnić, aby działać poprawnie w środowisku IDE.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Opis katalogu szablonu (pliki Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)  
 Zawiera omówienie szablonów plików opisu katalogów i wyjaśniono, jak działają w środowisku IDE w celu wyświetlania folderów, plików kreatora. vsz i plików szablonów, które są skojarzone z projektem w oknach dialogowych.  
  
 [Kreator (plik Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)  
 Wyjaśnia, w jaki sposób IDE uruchamia kreatorzy i wyświetla trzy części pliku. vsz.  
  
 [Interfejs kreatora (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)  
 Opisuje `IDTWizard` interfejs, który Kreator musi zaimplementować do pracy w środowisku IDE.  
  
 [Parametry kontekstu](../../extensibility/internals/context-parameters.md)  
 Wyjaśnia, w jaki sposób kreatory są implementowane i co się dzieje, gdy środowisko IDE przekazuje parametry kontekstu do implementacji.  
  
 [Parametry niestandardowe](../../extensibility/internals/custom-parameters.md)  
 Wyjaśnia, jak używać parametrów niestandardowych do kontrolowania operacji kreatora po uruchomieniu kreatora.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Typy projektów](../../extensibility/internals/project-types.md)  
 Zawiera łącza do dodatkowych tematów, które zawierają informacje o sposobach projektowania nowych typów projektów.  
  
 [Przewodnik: Tworzenie Kreatora](https://msdn.microsoft.com/library/adb41fe9-fcca-4e87-bf4f-bf2fa68e8b06)  
 Ilustruje sposób tworzenia kreatora.  
  
 [Rozszerzanie projektów](../../extensibility/extending-projects.md)  
 Opisuje sposób używania [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projektów i rozwiązań do organizowania plików kodu i plików zasobów oraz sposobu implementacji kontroli źródła.
