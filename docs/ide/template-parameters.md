---
title: Parametry szablonu projektu i elementu
ms.date: 01/02/2018
ms.topic: reference
helpviewer_keywords:
- Visual Studio templates, parameters
- template parameters [Visual Studio]
- project templates, parameters
- item templates, parameters
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 90035e99c13484bd1b49e59350489ed1090b5f4e
ms.sourcegitcommit: 673b9364fc9a96b027662dcb4cf5d61cab60ef11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69891267"
---
# <a name="template-parameters"></a>Parametry szablonu

Można zastąpić wartości w szablonie, podczas tworzenia wystąpienia szablonu. Aby skonfigurować tę funkcję, należy użyć *parametry szablonu*. Parametry szablonu może służyć do zastąpienia wartości, takich jak nazwy klas i przestrzenie nazw w szablonie. Kreator szablonu, który działa w tle, gdy użytkownik dodaje nowy element lub projekt zastępuje te parametry.

## <a name="declare-and-enable-template-parameters"></a>Deklarowanie i włączanie parametrów szablonu

Parametry szablonu są deklarowane w formacie $*parametru*$. Na przykład:

- $safeprojectname$

- $guid1$

- $guid5$

### <a name="enable-parameter-substitution-in-templates"></a>Włącz podstawianie parametrów w szablonach

1. W *.vstemplate* pliku szablonu, zlokalizuj `ProjectItem` element, który odpowiada elementowi, dla którego chcesz włączyć podmianę parametrów.

1. Ustaw atrybut `ReplaceParameters` elementu `ProjectItem` na `true`.

1. W pliku kodu dla elementu projektu dołącz parametry, tam gdzie jest to potrzebne. Na przykład następujący parametr określa, że bezpieczna Nazwa projektu jest używana dla przestrzeni nazw w pliku:

    ```csharp
    namespace $safeprojectname$
    ```

## <a name="reserved-template-parameters"></a>Zastrzeżone parametry szablonu

W poniższej tabeli wymieniono zastrzeżone parametry szablonu, które mogą być używane przez dowolny szablon:

|Parametr|Opis|
|---------------|-----------------|
|clrversion|Aktualna wersja środowiska uruchomieniowego języka wspólnego (CLR).|
|ext_*|`ext_` Dodaj prefiks do dowolnego parametru, aby odwołać się do zmiennych szablonu nadrzędnego. Na przykład `ext_safeprojectname`.|
|Identyfikator GUID [1 – 10]|Identyfikator GUID służący do zamienienia identyfikatora GUID w pliku projektu. Można określić maksymalnie 10 unikatowych identyfikatorów GUID (na przykład `guid1`).|
|Nazwa elementu|Nazwa pliku, w którym jest używany parametr.|
|NazwaKomputera|Bieżąca nazwa komputera (na przykład Computer01).|
|projectname|Nazwa podana przez użytkownika podczas tworzenia projektu.|
|registeredorganization|Wartość klucza rejestru z HKLM\Software\Microsoft\Windows NT\CurrentVersion\RegisteredOrganization.|
|rootnamespace|Główna przestrzeń nazw bieżącego projektu. Ten parametr dotyczy tylko szablonów elementów.|
|safeitemname|Analogicznie `itemname` jak w przypadku wszystkich niebezpiecznych znaków i spacji zastępowanych znakami podkreślenia.|
|safeitemrootname|Analogicznie `safeitemname`jak.|
|safeprojectname|Nazwa podana przez użytkownika podczas tworzenia projektu, ale z usuniętymi wszystkimi niebezpiecznymi znakami i spacjami.|
|czas|Bieżący czas w formacie DD/MM/RRRR 00:00:00.|
|SpecificSolutionName|Nazwa rozwiązania. W razie wybrania opcji „Utwórz katalog rozwiązania”, `SpecificSolutionName` ma nazwę rozwiązania. Jeżeli „Utwórz katalog rozwiązania” nie jest zaznaczone, `SpecificSolutionName` jest pusta.|
|USERDOMAIN|Bieżąca domena użytkownika.|
|Nazwa użytkownika|Bieżąca nazwa użytkownika.|
|webnamespace|Nazwa bieżącej witryny sieci Web. Ten parametr jest używany w szablonie formularza sieci web, aby zagwarantować unikalne nazwy klas. W przypadku witryny sieci Web w katalogu głównym serwera sieci web, ten parametr szablonu jest rozpoznawany jako katalog główny serwera sieci web.|
|Rok|Bieżący rok w formacie RRRR.|

> [!NOTE]
> Parametry szablonu uwzględniają wielkość liter.

## <a name="custom-template-parameters"></a>Parametry szablonu niestandardowego

Można określić własne parametry szablonu i wartości, oprócz parametrów zastrzeżonego szablonu domyślnego, które są używane podczas wymiany parametru. Aby uzyskać więcej informacji, zobacz [customparameters — element (szablony Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md).

## <a name="example-use-the-project-name-for-a-file-name"></a>Przykład: Użyj nazwy projektu dla nazwy pliku

Nazwy zmiennych plików dla elementów projektu można określić za pomocą parametru w `TargetFileName` atrybutu.

W poniższym przykładzie określono, że nazwa pliku wykonywalnego używa nazwy projektu, określonej przez `$projectname$`.

```xml
<TemplateContent>
    <ProjectItem
        ReplaceParameters="true"
        TargetFileName="$projectname$.exe">
            File1.exe
    </ProjectItem>
      ...
</TemplateContent>
```

## <a name="example-use-the-safe-project-name-for-the-namespace-name"></a>Przykład: Użyj bezpiecznej nazwy projektu dla nazwy przestrzeni nazw

Aby użyć bezpieczna Nazwa projektu dla przestrzeni nazw w pliku klasy C#, należy użyć następującej składni:

```csharp
namespace $safeprojectname$
{
    public class Class1
    {
        public Class1()
        { }
    }
}
```

W *.vstemplate* pliku szablonu projektu, obejmują `ReplaceParameters="true"` atrybutu, gdy odwołanie do pliku:

```xml
<TemplateContent>
    <ProjectItem ReplaceParameters="true">
        Class1.cs
    </ProjectItem>
    ...
</TemplateContent>
```

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Zastępowanie parametrów w szablonie](how-to-substitute-parameters-in-a-template.md)
- [Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)
- [Instrukcje: Tworzenie szablonów projektu](../ide/how-to-create-project-templates.md)
- [Odwołanie do schematu szablonu](../extensibility/visual-studio-template-schema-reference.md)
