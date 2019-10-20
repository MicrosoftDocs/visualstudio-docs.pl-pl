---
title: Definiowanie i Instalowanie rozszerzenia modelowania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending
- UML model, extending
ms.assetid: 82a58dc5-c7cf-4521-a6da-7ff09cd0de9d
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 66a9cdab1284d015e2ea76162d240b6a1232d90f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669921"
---
# <a name="define-and-install-a-modeling-extension"></a>Definiowanie i instalowanie rozszerzenia modelowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio można definiować rozszerzenia do diagramów modelowania. W ten sposób można dostosować diagramy i modele do własnych potrzeb. Można na przykład definiować polecenia menu, profile UML, ograniczenia walidacji i elementy przybornika. W jednym rozszerzeniu można zdefiniować kilka składników. Możesz również dystrybuować te rozszerzenia do innych użytkowników programu Visual Studio w postaci [rozszerzenia integracji z programem Visual Studio (VSIX)](http://go.microsoft.com/fwlink/?LinkId=160780). Można utworzyć VSIX przy użyciu projektu VSIX w programie Visual Studio.

## <a name="requirements"></a>Wymagania
 Zobacz [wymagania](../modeling/extend-uml-models-and-diagrams.md#Requirements).

 Aby sprawdzić, które wersje programu Visual Studio obsługują tę funkcję, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="creating-a-modeling-extension-solution"></a>Tworzenie rozwiązania do rozszerzenia modelowania
 Aby zdefiniować rozszerzenie modelowania, należy utworzyć rozwiązanie zawierające następujące projekty:

- Projekt rozszerzenia integracji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (VSIX). Spowoduje to wygenerowanie pliku, który działa jako Instalator składników rozszerzenia.

- Projekt biblioteki klas, wymagany dla składników, które zawierają kod programu.

  Jeśli chcesz utworzyć rozszerzenie, które ma kilka składników, możesz je opracować w jednym rozwiązaniu. Potrzebny jest tylko jeden projekt VSIX.

  Składniki, które nie wymagają kodu, takie jak niestandardowe elementy przybornika i niestandardowe profile UML, można dodać bezpośrednio do projektu VSIX bez użycia oddzielnych projektów biblioteki klas. Składniki wymagające kodu programu są łatwiejsze do zdefiniowania w osobnym projekcie biblioteki klas. Składniki wymagające obsługi gestów, poleceń menu i kodu sprawdzania poprawności.

#### <a name="to-create-a-class-library-project-for-menu-commands-gesture-handlers-or-validation"></a>Aby utworzyć projekt biblioteki klas dla poleceń menu, programów obsługi gestów lub walidacji

1. W menu **plik** wybierz polecenie **Nowy**, **projekt**.

2. W obszarze **zainstalowane szablony**wybierz **pozycję C# Wizualizacja** lub **Visual Basic**, a następnie wybierz pozycję **Biblioteka klas**.

#### <a name="to-create-a-vsix-project"></a>Aby utworzyć projekt VSIX

1. Jeśli tworzysz składnik z kodem, najłatwiej jest najpierw utworzyć projekt biblioteki klas. Kod zostanie dodany do tego projektu.

2. Utwórz projekt VSIX.

    1. W **Eksplorator rozwiązań**, w menu skrótów rozwiązania, wybierz **Dodaj**, **Nowy projekt**.

    2. W obszarze **zainstalowane szablony**rozwiń **pozycję C# Wizualizacja** lub **Visual Basic**, a następnie wybierz pozycję **rozszerzalność**. W środkowej kolumnie Wybierz pozycję **Projekt VSIX**.

3. Ustaw projekt VSIX jako projekt startowy rozwiązania.

    - W Eksplorator rozwiązań, w menu skrótów projektu VSIX, wybierz **Ustaw jako projekt startowy**.

4. Open **source. Extension. vsixmanifest**. Plik zostanie otwarty w edytorze manifestu.

5. Na karcie **metadane** Ustaw nazwę i pola opisowe dla VSIX.

6. Na karcie **Instalowanie obiektów docelowych** wybierz pozycję **nowe** i ustaw wersje programu Visual Studio jako elementy docelowe.

7. Na karcie **zasoby** Dodaj składniki do rozszerzenia programu Visual Studio.

    1. Wybierz pozycję **Nowy**.

    2. Dla składnika z kodem ustaw następujące pola w oknie dialogowym **Dodaj nowy element zawartości** :

        |||
        |-|-|
        |**Typ**  =|**Microsoft. VisualStudio. MefComponent**|
        |@No__t_1 **źródłowa**|**Projekt w bieżącym rozwiązaniu**|
        |@No__t_1 **projektu**|*Projekt biblioteki klas*|
        |**Osadź w tym folderze**  =|*ciągiem*|

         W przypadku innych typów składników zapoznaj się z linkami w następnej sekcji.

## <a name="developing-the-component"></a>Programowanie składnika
 Dla każdego składnika, takiego jak polecenie menu lub procedura obsługi gestu, należy zdefiniować oddzielną procedurę obsługi. Można umieścić kilka programów obsługi w tym samym projekcie biblioteki klas. W poniższej tabeli zestawiono różne rodzaje obsługi.

|Typ rozszerzenia|Temat|Jak każdy składnik jest zwykle zadeklarowany|
|--------------------|-----------|----------------------------------------------|
|Polecenie menu|[Definiowanie polecenia menu w diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|`[ClassDesignerExtension]`<br /><br /> `// or other diagram types`<br /><br /> `[Export(typeof(ICommandExtension))]`<br /><br /> `public class MyCommand : ICommandExtension`<br /><br /> `{...`|
|Przeciągnij i upuść lub kliknij dwukrotnie|[Definiowanie procedury obsługi gestów na diagramie modelowania](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)|`[ClassDesignerExtension]`<br /><br /> `// or other diagram types`<br /><br /> `[Export(typeof(IGestureExtension))]`<br /><br /> `public class MyGesture : IGestureExtension`<br /><br /> `{...`|
|Ograniczenie walidacji|[Definiowanie ograniczeń walidacji dla modeli UML](../modeling/define-validation-constraints-for-uml-models.md)|`[Export(typeof(     System.Action<ValidationContext, object>))]`<br /><br /> `[ValidationMethod(ValidationCategories.Save`<br /><br /> `&#124; ValidationCategories.Menu)]`<br /><br /> `public void ValidateSomething`<br /><br /> `(ValidationContext context, IClassifier elementToValidate)`<br /><br /> `{...}`|
|Procedura obsługi zdarzeń linku elementu pracy|[Definiowanie procedury obsługi linku elementu roboczego](../modeling/define-a-work-item-link-handler.md)|`[Export(typeof(ILinkedWorkItemExtension))]`<br /><br /> `public class MyWorkItemEventHandler : ILinkedWorkItemExtension`<br /><br /> `{...`|
|Profil UML|[Definiowanie profilu w celu rozszerzenia kodu UML](../modeling/define-a-profile-to-extend-uml.md)|(Do zdefiniowania)|
|Element przybornika|[Definiowanie niestandardowego elementu przybornika modelowania](../modeling/define-a-custom-modeling-toolbox-item.md)|(Do zdefiniowania)|

## <a name="running-an-extension-during-its-development"></a>Uruchamianie rozszerzenia w trakcie jego tworzenia

#### <a name="to-run-an-extension-during-its-development"></a>Aby uruchomić rozszerzenie podczas jego tworzenia

1. W menu **debugowanie** [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] wybierz **Rozpocznij debugowanie**.

     Kompilacja projektu i nowe wystąpienie [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] są uruchamiane w trybie eksperymentalnym.

    - Alternatywnie możesz wybrać opcję **Rozpocznij bez debugowania**. Pozwala to skrócić czas potrzebny do uruchomienia programu.

2. Utwórz lub Otwórz projekt modelowania w eksperymentalnym wystąpieniu programu Visual Studio i Utwórz lub Otwórz diagram.

     Twoje rozszerzenie zostanie załadowane i uruchomione.

3. Jeśli używasz narzędzia **Uruchom bez debugowania** , ale chcesz użyć debugera, Wróć do głównego wystąpienia programu Visual Studio. W menu **debugowanie** kliknij **Dołącz do procesu**. W oknie dialogowym Wybierz eksperymentalne wystąpienie programu Visual Studio, które ma nazwę programu **devenv**.

## <a name="Installing"></a>Instalowanie i odinstalowywanie rozszerzenia
 Wykonaj następujące kroki, aby uruchomić rozszerzenie w głównym wystąpieniu programu Visual Studio na własnym komputerze lub na innych komputerach.

1. Na komputerze Znajdź plik **. vsix** , który został skompilowany przez projekt rozszerzenia.

    1. W **Eksplorator rozwiązań**, w menu skrótów projektu, a następnie wybierz polecenie **Otwórz folder w Eksploratorze Windows**.

    2. Zlokalizuj plik **bin \\ \* \\** _YourProject_ **. vsix**

2. Skopiuj plik **. vsix** do komputera docelowego, na którym chcesz zainstalować rozszerzenie. Może to być własny komputer lub inny.

    - Na komputerze docelowym musi znajdować się jedna z wersji programu Visual Studio określona na karcie **cele instalacji** elementu **source. Extension. vsixmanifest**.

3. Na komputerze docelowym otwórz plik **. vsix** , na przykład klikając go dwukrotnie.

     Zostanie otwarty **Instalator rozszerzenia programu Visual Studio** , który zainstaluje rozszerzenie.

4. Uruchom lub Uruchom ponownie program Visual Studio.

#### <a name="to-uninstall-an-extension"></a>Aby odinstalować rozszerzenie

1. W menu **Narzędzia** kliknij pozycję **rozszerzenia i aktualizacje**.

2. Rozwiń **zainstalowane rozszerzenia**.

3. Wybierz rozszerzenie, a następnie kliknij przycisk **Odinstaluj**.

   Rzadko błędne rozszerzenie nie zostanie załadowane i tworzy raport w oknie błędu, ale nie jest wyświetlany w Menedżerze rozszerzeń. W takim przypadku można usunąć rozszerzenie, usuwając plik z następującej lokalizacji, gdzie *% LocalAppData%* jest zazwyczaj *dysk*: \Users \\*username*\AppData\Local:

   *% LocalAppData%* **\Microsoft\VisualStudio \\ [wersja] \Extensions**

## <a name="see-also"></a>Zobacz też
 [Zdefiniuj profil, aby zwiększyć UML](../modeling/define-a-profile-to-extend-uml.md) [Definiowanie niestandardowego elementu przybornika modelowania](../modeling/define-a-custom-modeling-toolbox-item.md) [Definiowanie ograniczeń walidacji dla modeli UML](../modeling/define-validation-constraints-for-uml-models.md) [Definiowanie polecenia menu na diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md)
