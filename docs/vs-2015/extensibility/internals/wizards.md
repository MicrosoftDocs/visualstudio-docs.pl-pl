---
title: Kreatorzy | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687628"
---
# <a name="wizards"></a>Kreatory
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Po utworzeniu kreatora, zazwyczaj chcesz dodać go do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zintegrowane środowisko projektowe (IDE), aby inne osoby mogą go używać. Pojawi się w Kreatorze dodano **Dodaj nowy projekt** lub **Dodaj nowy element** okien dialogowych. Aby wyświetlić **Dodaj nowy projekt** lub **Dodaj nowy element** okna dialogowego pola, kliknij prawym przyciskiem myszy otwartego rozwiązania w **Eksploratora rozwiązań**, wskaż polecenie **Dodaj**, i następnie kliknij przycisk **nowy projekt** lub **nowy element**.  
  
 Kreatorzy mogą być implementowane w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] aby powiadomić użytkowników, wybierz jedną z dostępnych wartości po otwarciu w widoku drzewa **Dodaj nowy projekt** okno dialogowe lub **Dodaj nowy element** okno dialogowe, lub po ich prawym przyciskiem myszy element **Eksploratora rozwiązań**.  
  
 W kreatora możesz podać opcji lokalizowania nazwę nowego projektu lub ites i możesz określić ikony, którą użytkownicy zobaczą, gdy wybierają kreatora. Możesz również kontrolować kolejność, w którym pojawią się nowe elementy, względem innych dostępnych elementów; elementy mają być zorganizowane alfabetycznie.  
  
 Możesz również dostarczyć kreatora, który rozpoczyna się inaczej, oparte na niestandardowych parametrów, które są przekazywane do kreatora po jego otwarciu.  
  
 W tematach w tej sekcji opisano pliki, które można zaimplementować, aby spowodować, że [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **Dodaj nowy projekt** i **Dodaj nowy element** oknach dialogowych, aby wyświetlić listę kreatora wśród dostępnych kreatorów i szablonów i wymagania które muszą spełniać kreatora, aby działać poprawnie w środowisku IDE.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Opis katalogu szablonu (pliki Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)  
 Omówienie szablonu katalogu plików opisu i wyjaśniono, jak działają w IDE, aby wyświetlić folderów, plików .vsz kreatora i plików szablonów, które są skojarzone z projektem w oknach dialogowych.  
  
 [Kreator (plik Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)  
 Wyjaśnia sposób uruchamiania kreatorów w IDE i zawiera trzy części pliku .vsz.  
  
 [Interfejs kreatora (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)  
 W tym artykule opisano `IDTWizard` interfejs, który musi implementować kreatorów, aby pracować w środowisku IDE.  
  
 [Parametry kontekstu](../../extensibility/internals/context-parameters.md)  
 Wyjaśnia implementacji kreatorów i zachowanie występujące podczas IDE przekazuje parametry kontekstu do wykonania.  
  
 [Parametry niestandardowe](../../extensibility/internals/custom-parameters.md)  
 Wyjaśnia, jak używać parametrów niestandardowych do kontroli działania kreatora, po uruchomieniu kreatora.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Typy projektów](../../extensibility/internals/project-types.md)  
 Zawiera łącza do dodatkowych tematów, które oferują informacji na temat sposobu projektowania nowych typów projektów.  
  
 [Przewodnik: Tworzenie kreatora](https://msdn.microsoft.com/library/adb41fe9-fcca-4e87-bf4f-bf2fa68e8b06)  
 Ilustruje sposób tworzenia kreatora.  
  
 [Rozszerzanie projektów](../../extensibility/extending-projects.md)  
 Opisuje sposób używania [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projekty i rozwiązania do organizowania plików kodu i plików zasobów i sposób implementowania kontroli źródła.
