---
title: 'Instrukcje: Tworzenie szablonów projektów | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ExportTemplateWizard
helpviewer_keywords:
- Visual Studio templates, creating project templates
- project templates, metadata files
- Visual Studio templates, project templates
- project templates, custom template locations
- project templates, creating
ms.assetid: a1a6999d-a34c-48a8-b1cf-027eb5c76398
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 918462bff3c2ac8dc57cb9c2c55a7d901707683c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60051547"
---
# <a name="how-to-create-project-templates"></a>Instrukcje: Tworzenie szablonów projektów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta procedura umożliwia utworzenie szablonu przy użyciu **Eksportuj szablon** kreatora, w którym są pakuje szablonu w formie pliku .zip. Można również utworzyć szablony w formacie pliku VSIX do wdrożenia ulepszone, za pomocą rozszerzenia Kreatora eksportowania szablonu lub za pomocą szablonów objęte [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)], lub można ręcznie utworzyć szablony.  
  
### <a name="to-create-a-custom-project-template-with-the-standard-export-template-wizard"></a>Tworzenie szablonu niestandardowego projektu przy użyciu standardowego kreatora Eksportuj szablon  
  
1. Utwórz projekt.  
  
    > [!NOTE]
    >  Gdy nazwy projektu, który będzie źródło szablonu, należy używać tylko znaków prawidłowego identyfikatora. Szablon wyeksportowany z projektu o nazwie nieprawidłowe znaki może spowodować błędy kompilacji w przyszłości projekty na podstawie szablonu. Aby uzyskać więcej informacji na prawidłowy identyfikator znaków, zobacz [zadeklarowane nazwy elementów](http://msdn.microsoft.com/library/09d8843b-c0dc-4afe-9dab-87c439a69e66).  
  
2. Edytuj projekt, dopóki nie jest gotowy do wyeksportowania jako szablon.  
  
3. Zgodnie z potrzebami edytować pliki kodu, aby wskazać, gdzie wymiany parametru powinny zostać wykonane. Aby uzyskać więcej informacji na temat zastępowania parametrów, zobacz [jak: Zastępowanie parametrów w szablonie](../ide/how-to-substitute-parameters-in-a-template.md).  
  
4. Na **pliku** menu, kliknij przycisk **Eksportuj szablon**. **Eksportuj szablon** zostanie otwarty Kreator.  
  
5. Kliknij przycisk **projektu szablonu**.  
  
6. Jeśli masz więcej niż jeden projekt w bieżącym rozwiązaniu, wybierz projekty, do których mają zostać wyeksportowane do szablonu.  
  
7. Kliknij przycisk **Dalej**.  
  
8. Wybierz ikonę i obrazu podglądu dla szablonu. Będą one wyświetlane na **nowy projekt** okno dialogowe.  
  
9. Wprowadź nazwę i opis szablonu.  
  
10. Kliknij przycisk **Zakończ**. Projekt jest wyeksportowany do pliku zip i umieszczane w lokalizacji określonym produktem wyjściowym i, jeśli zaznaczone, zaimportowany do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     Jeśli masz [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] zainstalowane, można opakować ukończony szablon w pliku .vsix dla wdrożenia przy użyciu **projekt VSIX** szablonu. Aby uzyskać więcej informacji, zobacz [rozpoczęcie korzystania z szablonu projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)   
 [Instrukcje: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md)
