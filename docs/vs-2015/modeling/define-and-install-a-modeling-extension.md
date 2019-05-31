---
title: Definiowanie i instalowanie rozszerzenia modelowania | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending
- UML model, extending
ms.assetid: 82a58dc5-c7cf-4521-a6da-7ff09cd0de9d
caps.latest.revision: 39
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cf370b4ca0e0a4d14c482c6ece46b79d2d224d34
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60049740"
---
# <a name="define-and-install-a-modeling-extension"></a>Definiowanie i instalowanie rozszerzenia modelowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio można zdefiniować rozszerzenia do diagramów modelowania. W ten sposób można dostosować do własnych potrzeb diagramów i modeli. Na przykład można zdefiniować polecenia menu, profilów UML, ograniczenia sprawdzania poprawności i elementy do przybornika. Można zdefiniować kilka składników, jednego rozszerzenia. Mogą również rozpowszechniać te rozszerzenia innym użytkownikom programu Visual Studio w formie [Visual Studio Integration rozszerzenie (VSIX)](http://go.microsoft.com/fwlink/?LinkId=160780). Można utworzyć VSIX używania projektu VSIX w programie Visual Studio.  
  
## <a name="requirements"></a>Wymagania  
 Zobacz [wymagania](../modeling/extend-uml-models-and-diagrams.md#Requirements).  
  
 Aby zobaczyć, które wersje programu Visual Studio obsługuje tę funkcję, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="creating-a-modeling-extension-solution"></a>Tworzenie rozwiązania rozszerzenia modelowania  
 Aby zdefiniować rozszerzenia modelowania, należy utworzyć rozwiązanie zawierające projekty te:  
  
- A [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Integration rozszerzenie (VSIX) projektu. Spowoduje to wygenerowanie pliku, który działa jako Instalator składników Twojego rozszerzenia.  
  
- Projekt biblioteki klas, wymaganych dla składników, które zawierają kod programu.  
  
  Jeśli chcesz utworzyć rozszerzenie, które zawiera kilka składników, możesz tworzyć je w ramach jednego rozwiązania. Konieczne jest tylko jeden projekt VSIX.  
  
  Składniki, które nie wymagają kodu, takich jak elementy do przybornika niestandardowego i niestandardowych profilów UML, można dodać bezpośrednio do projektu VSIX, bez użycia osobnej klasy biblioteki projektów. Składniki, które wymagają kodu programu łatwiej są zdefiniowane w projekcie osobnej klasy biblioteki. Składniki, które wymagają kodu obejmują program obsługi gestów, polecenia menu i kod sprawdzania poprawności.  
  
#### <a name="to-create-a-class-library-project-for-menu-commands-gesture-handlers-or-validation"></a>Aby utworzyć projekt biblioteki klas dla polecenia menu, programy obsługi gestu lub sprawdzania poprawności  
  
1. Na **pliku** menu, wybierz **New**, **projektu**.  
  
2. W obszarze **zainstalowane szablony**, wybierz opcję **Visual C#** lub **języka Visual Basic**, następnie wybierz **biblioteki klas**.  
  
#### <a name="to-create-a-vsix-project"></a>Aby utworzyć projekt VSIX  
  
1. W przypadku tworzenia składnika z kodem najłatwiej najpierw Utwórz projekt biblioteki klas. Dodasz kod do tego projektu.  
  
2. Utwórz projekt VSIX.  
  
    1. W **Eksploratora rozwiązań**, w menu skrótów rozwiązania wybierz **Dodaj**, **nowy projekt**.  
  
    2. W obszarze **zainstalowane szablony**, rozwiń węzeł **Visual C#** lub **języka Visual Basic**, a następnie wybierz **rozszerzalności**. W środkowej kolumnie Wybierz **projekt VSIX**.  
  
3. Ustaw projekt VSIX jako projekt startowy rozwiązania.  
  
    - W Eksploratorze rozwiązań w menu skrótów projektu VSIX wybierz **Ustaw jako projekt startowy**.  
  
4. Otwórz **source.extension.vsixmanifest**. Plik zostanie otwarty w edytorze manifestu.  
  
5. Na **metadanych** kartę, należy ustawić pola nazwy i opisu VSIX.  
  
6. Na **Instaluj obiekty docelowe** kartę, wybrać **New** i ustaw wersje programu Visual Studio jako obiekty docelowe.  
  
7. Na **zasoby** kartę, Dodaj składniki do rozszerzenia programu Visual Studio.  
  
    1. Wybierz **nowe**.  
  
    2. Składnik z kodem, ustaw dla tych pól w **Dodaj nowy zasób** okno dialogowe:  
  
        |||  
        |-|-|  
        |**Typ** =|**Microsoft.VisualStudio.MefComponent**|  
        |**Źródło** =|**Projekt w bieżącym rozwiązaniu**|  
        |**Project** =|*Projekt biblioteki klas*|  
        |**Osadzanie w tym folderze** =|*(pusty)*|  
  
         Dla innych typów składników Zobacz linki w następnej sekcji.  
  
## <a name="developing-the-component"></a>Tworzenie składnika  
 Dla każdego składnika, takiego jak program obsługi polecenia lub gestu menu należy określić oddzielny program obsługi. Możesz umieścić kilka programów obsługi, w tym samym projekcie biblioteki klas. W poniższej tabeli przedstawiono różne rodzaje obsługi.  
  
|Typ rozszerzenia|Temat|Jak zwykle jest zadeklarowana każdego składnika|  
|--------------------|-----------|----------------------------------------------|  
|Polecenia menu|[Definiowanie polecenia menu w diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|`[ClassDesignerExtension]`<br /><br /> `// or other diagram types`<br /><br /> `[Export(typeof(ICommandExtension))]`<br /><br /> `public class MyCommand : ICommandExtension`<br /><br /> `{...`|  
|Przeciągnij i upuść lub kliknij dwukrotnie plik|[Definiowanie procedury obsługi gestów na diagramie modelowania](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)|`[ClassDesignerExtension]`<br /><br /> `// or other diagram types`<br /><br /> `[Export(typeof(IGestureExtension))]`<br /><br /> `public class MyGesture : IGestureExtension`<br /><br /> `{...`|  
|Ograniczenie sprawdzania poprawności|[Definiowanie ograniczeń walidacji dla modeli UML](../modeling/define-validation-constraints-for-uml-models.md)|`[Export(typeof(     System.Action<ValidationContext, object>))]`<br /><br /> `[ValidationMethod(ValidationCategories.Save`<br /><br /> `&#124; ValidationCategories.Menu)]`<br /><br /> `public void ValidateSomething`<br /><br /> `(ValidationContext context, IClassifier elementToValidate)`<br /><br /> `{...}`|  
|Procedury obsługi zdarzeń łącza elementu roboczego|[Definiowanie procedury obsługi linku elementu roboczego](../modeling/define-a-work-item-link-handler.md)|`[Export(typeof(ILinkedWorkItemExtension))]`<br /><br /> `public class MyWorkItemEventHandler : ILinkedWorkItemExtension`<br /><br /> `{...`|  
|Profil UML|[Definiowanie profilu w celu rozszerzenia kodu UML](../modeling/define-a-profile-to-extend-uml.md)|(Do ustalenia)|  
|Element przybornika|[Definiowanie niestandardowego elementu przybornika modelowania](../modeling/define-a-custom-modeling-toolbox-item.md)|(Do ustalenia)|  
  
## <a name="running-an-extension-during-its-development"></a>Uruchamianie rozszerzenia podczas jego tworzenia.  
  
#### <a name="to-run-an-extension-during-its-development"></a>Aby uruchomić rozszerzenia podczas jego tworzenia.  
  
1. W [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] **debugowania** menu, wybierz **Rozpocznij debugowanie**.  
  
     Kompilacje projektu, a nowe wystąpienie klasy [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] jest uruchamiany w trybie doświadczalnym.  
  
    - Alternatywnie można wybrać **Rozpocznij bez debugowania**. Zmniejsza to czas potrzebny do uruchomienia programu.  
  
2. Utwórz lub Otwórz projekt modelowania w doświadczalnym wystąpieniu programu Visual Studio i Utwórz lub Otwórz diagram.  
  
     Rozszerzenie zostanie obciążenia i uruchom.  
  
3. Jeśli użyto **Rozpocznij bez debugowania** , ale chcesz użyć debugera, wróć do głównego wystąpienia programu Visual Studio. Na **debugowania** menu, kliknij przycisk **dołączyć do procesu**. W oknie dialogowym Wybierz doświadczalnym wystąpieniu programu Visual Studio, która zawiera nazwę programu **devenv**.  
  
## <a name="Installing"></a> Instalowanie i odinstalowywanie rozszerzenia  
 Wykonaj poniższe kroki, aby uruchomić rozszerzenia w głównym wystąpieniu programu Visual Studio na komputerze lokalnym lub na innych komputerach.  
  
1. Na komputerze, należy znaleźć **.vsix** pliku, który został zbudowany przez projekt rozszerzenia.  
  
    1. W **Eksploratora rozwiązań**, w menu skrótów projektu, a następnie wybierz **Otwórz Folder w Eksploratorze Windows**.  
  
    2. Zlokalizuj plik **bin\\\*\\** _YourProject_ **.vsix**  
  
2. Kopiuj **.vsix** plik na komputer docelowy, na którym chcesz zainstalować rozszerzenie. Może to być Twój własny komputer lub innej.  
  
    - Komputer docelowy musi mieć jedną z wersji programu Visual Studio, którą podano na **elementy docelowe instalacji** karcie **source.extension.vsixmanifest**.  
  
3. Na komputerze docelowym, otwórz **.vsix** pliku, na przykład, klikając go dwukrotnie.  
  
     **Instalator rozszerzenia programu Visual Studio** otwiera i instaluje rozszerzenia.  
  
4. Uruchom lub uruchom ponownie program Visual Studio.  
  
#### <a name="to-uninstall-an-extension"></a>Aby odinstalować rozszerzenie  
  
1. Na **narzędzia** menu, kliknij przycisk **rozszerzenia i aktualizacje**.  
  
2. Rozwiń **zainstalowanych rozszerzeń**.  
  
3. Zaznacz rozszerzenie a następnie kliknij przycisk **Odinstaluj**.  
  
   Rzadko wadliwe rozszerzenie nie ładuje się i tworzy raport w oknie błędów, ale nie są wyświetlane w Menedżerze rozszerzeń. W takim przypadku można usunąć rozszerzenie poprzez usunięcie pliku z następującej lokalizacji gdzie *% LocalAppData %* jest zazwyczaj *DriveName*: \Users\\*nazwyużytkownika*\AppData\Local:  
  
   *% LocalAppData %* **\Microsoft\VisualStudio\\\Extensions [wersja]**  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie profilu w celu rozszerzenia UML](../modeling/define-a-profile-to-extend-uml.md)   
 [Definiowanie niestandardowego elementu przybornika modelowania](../modeling/define-a-custom-modeling-toolbox-item.md)   
 [Definiowanie ograniczeń walidacji dla modeli UML](../modeling/define-validation-constraints-for-uml-models.md)   
 [Definiowanie polecenia menu w diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md)
