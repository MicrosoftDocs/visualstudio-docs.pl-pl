---
title: Parametry szablonu projektu i elementu
ms.date: 01/02/2018
ms.topic: reference
helpviewer_keywords:
- Visual Studio templates, parameters
- template parameters [Visual Studio]
- project templates, parameters
- item templates, parameters
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 445a4fa7847ea5c9a5cb64da09cf54c763e86d16
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647399"
---
# <a name="template-parameters"></a>Parametry szablonu

Możesz zamienić wartości w szablonie podczas tworzenia wystąpienia szablonu. Aby skonfigurować tę funkcję, użyj *parametrów szablonu*. Parametry szablonu mogą służyć do zastępowania wartości takich jak nazwy klas i przestrzenie nazw w szablonie. Kreator szablonów, który jest uruchamiany w tle, gdy użytkownik doda nowy element lub projekt zastępuje te parametry.

## <a name="declare-and-enable-template-parameters"></a>Deklarowanie i włączanie parametrów szablonu

Parametry szablonu są zadeklarowane w formacie $*Parameter*$. Na przykład:

- $safeprojectname$

- $guid1$

- $guid5$

### <a name="enable-parameter-substitution-in-templates"></a>Włącz podstawianie parametrów w szablonach

1. W pliku *. vstemplate* szablonu znajdź element `ProjectItem`, który odnosi się do elementu, dla którego chcesz włączyć zastąpienie parametrów.

1. Ustaw atrybut `ReplaceParameters` elementu `ProjectItem` na `true`.

1. W pliku kodu dla elementu projektu dołącz parametry, tam gdzie jest to potrzebne. Na przykład, następujący parametr określa, że bezpieczna nazwa projektu jest używana dla przestrzeni nazw w pliku:

    ```csharp
    namespace $safeprojectname$
    ```

## <a name="reserved-template-parameters"></a>Zastrzeżone parametry szablonu

W poniższej tabeli wymieniono zastrzeżone parametry szablonu, które mogą być używane przez dowolny szablon:

|Parametr|Opis|
|---------------|-----------------|
|CLRVERSION|Aktualna wersja środowiska uruchomieniowego języka wspólnego (CLR).|
|ext_*|Dodaj prefiks `ext_` do dowolnego parametru, aby odwołać się do zmiennych szablonu nadrzędnego. Na przykład `ext_safeprojectname`.|
|Identyfikator GUID [1-10]|Identyfikator GUID służący do zamienienia identyfikatora GUID w pliku projektu. Można określić maksymalnie 10 unikatowych identyfikatorów GUID (na przykład `guid1`).|
|itemName|Nazwa pliku, w którym jest używany parametr.|
|elementu|Bieżąca nazwa komputera (na przykład Computer01).|
|ProjectName|Nazwa podana przez użytkownika podczas tworzenia projektu.|
|RegisteredOrganization|Wartość klucza rejestru z HKLM\Software\Microsoft\Windows NT\CurrentVersion\RegisteredOrganization.|
|RootNamespace|Główna przestrzeń nazw bieżącego projektu. Ten parametr dotyczy tylko szablonów elementów.|
|safeitemname|Analogicznie jak `itemname`, ale ze wszystkimi niebezpiecznymi znakami i spacjami zastępowanymi znakami podkreślenia.|
|safeitemrootname|Taki sam jak `safeitemname`.|
|safeprojectname|Nazwa podana przez użytkownika podczas tworzenia projektu, ale z usuniętymi wszystkimi niebezpiecznymi znakami i spacjami.|
|czas|Bieżący czas w formacie DD/MM/RRRR 00:00:00.|
|specifiedSolutionName|Nazwa rozwiązania. W razie wybrania opcji „Utwórz katalog rozwiązania”, `specifiedSolutionName` ma nazwę rozwiązania. Jeżeli „Utwórz katalog rozwiązania” nie jest zaznaczone, `specifiedSolutionName` jest pusta.|
|userdomain|Bieżąca domena użytkownika.|
|uż|Bieżąca nazwa użytkownika.|
|webnazw|Nazwa bieżącej witryny sieci Web. Ten parametr jest używany w szablonie formularza sieci Web w celu zagwarantowania unikatowych nazw klas. Jeśli witryna internetowa znajduje się w katalogu głównym serwera sieci Web, ten parametr szablonu jest rozpoznawany jako katalog główny serwera sieci Web.|
|czteroletniego|Bieżący rok w formacie RRRR.|

> [!NOTE]
> Parametry szablonu uwzględniają wielkość liter.

## <a name="custom-template-parameters"></a>Parametry szablonu niestandardowego

Oprócz domyślnych parametrów szablonu zarezerwowanych, które są używane podczas zamiany parametru, można określić własne parametry i wartości szablonu. Aby uzyskać więcej informacji, zobacz [CustomParameters — element (szablony Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md).

## <a name="example-use-the-project-name-for-a-file-name"></a>Przykład: Użyj nazwy projektu dla nazwy pliku

Można określić zmienne nazwy plików dla elementów projektu przy użyciu parametru w atrybucie `TargetFileName`.

Poniższy przykład określa, że nazwa pliku wykonywalnego używa nazwy projektu, określonej przez `$projectname$`.

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

Aby użyć nazwy projektu bezpiecznego dla przestrzeni nazw w pliku C# klasy, należy użyć następującej składni:

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

W pliku *. vstemplate* szablonu projektu należy uwzględnić atrybut `ReplaceParameters="true"` podczas odwoływania się do pliku:

```xml
<TemplateContent>
    <ProjectItem ReplaceParameters="true">
        Class1.cs
    </ProjectItem>
    ...
</TemplateContent>
```

## <a name="see-also"></a>Zobacz także

- [Instrukcje: zastępowanie parametrów w szablonie](how-to-substitute-parameters-in-a-template.md)
- [Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)
- [Instrukcje: Tworzenie szablonów projektu](../ide/how-to-create-project-templates.md)
- [Dokumentacja schematu szablonu](../extensibility/visual-studio-template-schema-reference.md)
