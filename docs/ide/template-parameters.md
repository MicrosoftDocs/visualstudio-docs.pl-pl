---
title: Parametry szablonu projektu i elementu
ms.date: 01/02/2018
ms.topic: reference
helpviewer_keywords:
- Visual Studio templates, parameters
- template parameters [Visual Studio]
- project templates, parameters
- item templates, parameters
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 7076e8f5718e44cc382eb0768e6456dbd6ee5664
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "78169368"
---
# <a name="template-parameters"></a>Parametry szablonu

Wartości w szablonie można zastąpić podczas tworzenia wystąpienia szablonu. Aby skonfigurować tę funkcję, należy użyć *parametrów szablonu*. Parametry szablonu mogą służyć do zastępowania wartości, takich jak nazwy klas i przestrzenie nazw w szablonie. Kreator szablonów, który działa w tle, gdy użytkownik dodaje nowy element lub projekt zastępuje te parametry.

## <a name="declare-and-enable-template-parameters"></a>Deklarowanie i włączanie parametrów szablonu

Parametry szablonu są zadeklarowane w formacie $*parametr*$. Przykład:

- $safeprojectname$

- $guid1$

- $guid5$

### <a name="enable-parameter-substitution-in-templates"></a>Włączanie podstawiania parametrów w szablonach

1. W pliku *vstemplate* szablonu znajdź `ProjectItem` element odpowiadający elementowi, dla którego chcesz włączyć zastępowanie parametrów.

1. Ustaw atrybut `ReplaceParameters` elementu `ProjectItem` na `true`.

1. W pliku kodu dla elementu projektu dołącz parametry, tam gdzie jest to potrzebne. Na przykład następujący parametr określa, że bezpieczna nazwa projektu jest używana dla obszaru nazw w pliku:

    ```csharp
    namespace $safeprojectname$
    ```

## <a name="reserved-template-parameters"></a>Parametry szablonu zarezerwowanego

W poniższej tabeli wymieniono parametry szablonu zastrzeżonego, które mogą być używane przez dowolny szablon:

|Parametr|Opis|
|---------------|-----------------|
|clrversion (wersja clrversion)|Aktualna wersja środowiska uruchomieniowego języka wspólnego (CLR).|
|ext_*|Dodaj `ext_` prefiks do dowolnego parametru, aby odwoływać się do zmiennych szablonu nadrzędnego. Na przykład `ext_safeprojectname`.|
|guid[1-10]|Identyfikator GUID służący do zamienienia identyfikatora GUID w pliku projektu. Można określić maksymalnie 10 unikatowych identyfikatorów `guid1`GUID (na przykład ).|
|Itemname|Nazwa pliku, w którym parametr jest używany.|
|Machinename|Bieżąca nazwa komputera (na przykład Computer01).|
|Nazwaprojektu|Nazwa podana przez użytkownika podczas tworzenia projektu.|
|zarejestrowana organizacja|Wartość klucza rejestru z HKLM\Software\Microsoft\Windows NT\CurrentVersion\RegisteredOrganization.|
|Rootnamespace|Główna przestrzeń nazw bieżącego projektu. Ten parametr dotyczy tylko szablonów elementów.|
|nazwa safeitemname|Tak `itemname` samo jak w razie wszystkich niebezpiecznych znaków i spacji zastąpionych znakami podkreślenia.|
|safeitemrootname|Tak `safeitemname`samo jak .|
|safeprojectname|Nazwa podana przez użytkownika podczas tworzenia projektu, ale z usuniętymi wszystkimi niebezpiecznymi znakami i spacjami.|
|time|Bieżący czas w formacie DD/MM/RRRR 00:00:00.|
|specifiedsolutionname|Nazwa rozwiązania. W razie wybrania opcji „Utwórz katalog rozwiązania”, `specifiedsolutionname` ma nazwę rozwiązania. Jeżeli „Utwórz katalog rozwiązania” nie jest zaznaczone, `specifiedsolutionname` jest pusta.|
|userdomain|Bieżąca domena użytkownika.|
|nazwa użytkownika|Bieżąca nazwa użytkownika.|
|nazwa internetowa|Nazwa bieżącej strony internetowej. Ten parametr jest używany w szablonie formularza sieci web w celu zagwarantowania unikatowych nazw klas. Jeśli witryna sieci Web znajduje się w katalogu głównym serwera sieci web, ten parametr szablonu jest rozpoznawany w katalogu głównym serwera sieci web.|
|rok|Bieżący rok w formacie RRRR.|

> [!NOTE]
> Parametry szablonu uwzględniają wielkość liter.

## <a name="custom-template-parameters"></a>Parametry szablonu niestandardowego

Oprócz domyślnych parametrów szablonu zarezerwowanego, które są używane podczas zastępowania parametrów, można określić własne parametry i wartości szablonu. Aby uzyskać więcej informacji, zobacz [Element CustomParameters (szablony programu Visual Studio).](../extensibility/customparameters-element-visual-studio-templates.md)

## <a name="example-use-the-project-name-for-a-file-name"></a>Przykład: Używanie nazwy projektu dla nazwy pliku

Nazwy plików zmiennych dla elementów projektu można `TargetFileName` określić przy użyciu parametru w atrybucie.

Poniższy przykład określa, że nazwa pliku wykonywalnego `$projectname$`używa nazwy projektu, określonej przez program .

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

## <a name="example-use-the-safe-project-name-for-the-namespace-name"></a>Przykład: Użyj nazwy bezpiecznego projektu dla nazwy obszaru nazw

Aby użyć bezpiecznej nazwy projektu dla obszaru nazw w pliku klasy C#, należy użyć następującej składni:

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

W pliku *vstemplate* dla szablonu projektu `ReplaceParameters="true"` uwzględnij atrybut podczas odwoływania się do pliku:

```xml
<TemplateContent>
    <ProjectItem ReplaceParameters="true">
        Class1.cs
    </ProjectItem>
    ...
</TemplateContent>
```

## <a name="see-also"></a>Zobacz też

- [Jak: Zastępowanie parametrów w szablonie](how-to-substitute-parameters-in-a-template.md)
- [Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)
- [Jak: Tworzenie szablonów projektów](../ide/how-to-create-project-templates.md)
- [Odwołanie do schematu szablonu](../extensibility/visual-studio-template-schema-reference.md)
