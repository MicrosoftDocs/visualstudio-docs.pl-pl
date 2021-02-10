---
title: Parametry szablonu projektu i elementu
description: Dowiedz się, w jaki sposób używać parametrów szablonu do zastępowania wartości w szablonie podczas tworzenia wystąpienia szablonu.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: reference
helpviewer_keywords:
- Visual Studio templates, parameters
- template parameters [Visual Studio]
- project templates, parameters
- item templates, parameters
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 133fbec68ff0e6b04793c2e168c730ee37024ad4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970652"
---
# <a name="template-parameters"></a>Parametry szablonu

Możesz zamienić wartości w szablonie podczas tworzenia wystąpienia szablonu. Aby skonfigurować tę funkcję, użyj *parametrów szablonu*. Parametry szablonu mogą służyć do zastępowania wartości takich jak nazwy klas i przestrzenie nazw w szablonie. Kreator szablonów, który jest uruchamiany w tle, gdy użytkownik doda nowy element lub projekt zastępuje te parametry.

## <a name="declare-and-enable-template-parameters"></a>Deklarowanie i włączanie parametrów szablonu

Parametry szablonu są zadeklarowane w formacie $*Parameter*$. Na przykład:

- $safeprojectname$

- $guid1$

- $guid5$

### <a name="enable-parameter-substitution-in-templates"></a>Włącz podstawianie parametrów w szablonach

1. W pliku *. vstemplate* szablonu Znajdź `ProjectItem` element, który odnosi się do elementu, dla którego chcesz włączyć zastąpienie parametrów.

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
|ext_ *|Dodaj `ext_` prefiks do dowolnego parametru, aby odwołać się do zmiennych szablonu nadrzędnego. Na przykład `ext_safeprojectname`.|
|Identyfikator GUID [1-10]|Identyfikator GUID służący do zamienienia identyfikatora GUID w pliku projektu. Można określić maksymalnie 10 unikatowych identyfikatorów GUID (na przykład `guid1` ).|
|itemName|Nazwa pliku, w którym jest używany parametr.|
|elementu|Bieżąca nazwa komputera (na przykład Computer01).|
|ProjectName|Nazwa podana przez użytkownika podczas tworzenia projektu.|
|RegisteredOrganization|Wartość klucza rejestru z HKLM\Software\Microsoft\Windows NT\CurrentVersion\RegisteredOrganization.|
|RootNamespace|Główna przestrzeń nazw bieżącego projektu. Ten parametr dotyczy tylko szablonów elementów.|
|safeitemname|Analogicznie jak `itemname` w przypadku wszystkich niebezpiecznych znaków i spacji zastępowanych znakami podkreślenia.|
|safeitemrootname|Analogicznie jak `safeitemname` .|
|safeprojectname|Nazwa podana przez użytkownika podczas tworzenia projektu, ale z usuniętymi wszystkimi niebezpiecznymi znakami i spacjami.|
|time|Bieżący czas w formacie DD/MM/RRRR 00:00:00.|
|specifiedsolutionname|Nazwa rozwiązania. W razie wybrania opcji „Utwórz katalog rozwiązania”, `specifiedsolutionname` ma nazwę rozwiązania. Jeżeli „Utwórz katalog rozwiązania” nie jest zaznaczone, `specifiedsolutionname` jest pusta.|
|userdomain|Bieżąca domena użytkownika.|
|nazwa użytkownika|Bieżąca nazwa użytkownika.|
|webnazw|Nazwa bieżącej witryny sieci Web. Ten parametr jest używany w szablonie formularza sieci Web w celu zagwarantowania unikatowych nazw klas. Jeśli witryna internetowa znajduje się w katalogu głównym serwera sieci Web, ten parametr szablonu jest rozpoznawany jako katalog główny serwera sieci Web.|
|rok|Bieżący rok w formacie RRRR.|

> [!NOTE]
> Parametry szablonu uwzględniają wielkość liter.

## <a name="custom-template-parameters"></a>Parametry szablonu niestandardowego

Oprócz domyślnych parametrów szablonu zarezerwowanych, które są używane podczas zamiany parametru, można określić własne parametry i wartości szablonu. Aby uzyskać więcej informacji, zobacz [CustomParameters — element (szablony Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md).

## <a name="example-use-the-project-name-for-a-file-name"></a>Przykład: Użyj nazwy projektu dla nazwy pliku

Można określić zmienne nazwy plików dla elementów projektu przy użyciu parametru w `TargetFileName` atrybucie.

Poniższy przykład określa, że nazwa pliku wykonywalnego używa nazwy projektu, określonej przez `$projectname$` .

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

Aby użyć bezpiecznej nazwy projektu dla przestrzeni nazw w pliku klasy C#, należy użyć następującej składni:

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

W pliku *. vstemplate* szablonu projektu Dołącz `ReplaceParameters="true"` atrybut podczas odwoływania się do pliku:

```xml
<TemplateContent>
    <ProjectItem ReplaceParameters="true">
        Class1.cs
    </ProjectItem>
    ...
</TemplateContent>
```

## <a name="see-also"></a>Zobacz też

- [Instrukcje: zastępowanie parametrów w szablonie](how-to-substitute-parameters-in-a-template.md)
- [Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)
- [Instrukcje: Tworzenie szablonów projektu](../ide/how-to-create-project-templates.md)
- [Dokumentacja schematu szablonu](../extensibility/visual-studio-template-schema-reference.md)
