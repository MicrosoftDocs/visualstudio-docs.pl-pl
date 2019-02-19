---
title: Parametry szablonu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, parameters
- template parameters [Visual Studio]
- project templates, parameters
- item templates, parameters
ms.assetid: 1b567143-08c6-4d7a-b484-49f0671754fe
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1433d9ba1f207a0f86902d7afd56db6476b1fd56
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54787095"
---
# <a name="template-parameters"></a>Parametry szablonu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Przy użyciu parametrów w szablonach, można zamienić wartości kluczowych części szablonu, na przykład nazwy klas i przestrzenie nazw, przy tworzeniu wystąpienia szablonu. Parametry te są zastępowane przez Kreatora szablonów, który działa w tle, gdy użytkownik kliknie **OK** w **nowy projekt** lub **Dodaj nowy element** okien dialogowych.  
  
## <a name="declaring-and-enabling-template-parameters"></a>Deklarowanie i włączanie parametrów szablonu  
 Parametry szablonu są deklarowane w formacie $*parametru*$. Na przykład:  
  
-   $safeprojectname$  
  
-   $guid1$  
  
-   $guid5$  
  
#### <a name="to-enable-parameter-substitution-in-templates"></a>Aby włączyć podstawienie parametru w szablonach  
  
1.  W pliku .vstemplate szablonu zlokalizuj element `ProjectItem`, który odpowiada elementowi, dla którego chcesz włączyć podmianę parametrów.  
  
2.  Ustaw atrybut `ReplaceParameters` elementu `ProjectItem` na `true`.  
  
3.  W pliku kodu dla elementu projektu dołącz parametry, tam gdzie jest to potrzebne. Na przykład, następujący parametr określa, że bezpieczna nazwa projektu będzie używana dla przestrzeni nazw w pliku:  
  
    ```  
    namespace $safeprojectname$  
    ```  
  
## <a name="reserved-template-parameters"></a>Zastrzeżone parametry szablonu  
 Poniższa tabela zawiera listę zastrzeżonych parametrów szablonu, które mogą być używane przez dowolny szablon.  
  
> [!NOTE]
>  Parametry szablonu uwzględniają wielkość liter.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`clrversion`|Aktualna wersja środowiska uruchomieniowego języka wspólnego (CLR).|  
|`GUID [1-10]`|Identyfikator GUID służący do zamienienia identyfikatora GUID w pliku projektu. Można określić do dziesięciu unikatowych identyfikatorów GUID (na przykład `guid1)`.|  
|`itemname`|Nazwa podana przez użytkownika w **Dodaj nowy element** okno dialogowe.|  
|`machinename`|Bieżąca nazwa komputera (na przykład Computer01).|  
|`projectname`|Nazwa podana przez użytkownika w **nowy projekt** okno dialogowe.|  
|`registeredorganization`|Wartość klucza rejestru z HKLM\Software\Microsoft\Windows NT\CurrentVersion\RegisteredOrganization.|  
|`rootnamespace`|Główna przestrzeń nazw bieżącego projektu. Ten parametr dotyczy tylko szablonów elementów.|  
|`safeitemname`|Nazwa podana przez użytkownika w **Dodaj nowy element** okno dialogowe, za pomocą wszystkich niebezpiecznych znaków i usunięte spacje.|  
|`safeprojectname`|Nazwa podana przez użytkownika w **nowy projekt** okno dialogowe, za pomocą wszystkich niebezpiecznych znaków i usunięte spacje.|  
|`time`|Bieżący czas w formacie DD/MM/RRRR 00:00:00.|  
|`SpecificSolutionName`|Nazwa rozwiązania. W razie wybrania opcji „Utwórz katalog rozwiązania”, `SpecificSolutionName` ma nazwę rozwiązania. Jeżeli „Utwórz katalog rozwiązania” nie jest zaznaczone, `SpecificSolutionName` jest pusta.|  
|`userdomain`|Bieżąca domena użytkownika.|  
|`username`|Bieżąca nazwa użytkownika.|  
|`webnamespace`|Nazwa bieżącej witryny sieci Web. Ten parametr jest używany w szablonie formularza sieci Web, aby zagwarantować unikalne nazwy klas. Jeśli witryna sieci Web jest w katalogu głównym serwera sieci Web, ten parametr szablonu jest rozpoznawany jako należący do katalogu głównego serwera sieci Web.|  
|`year`|Bieżący rok w formacie RRRR.|  
  
## <a name="custom-template-parameters"></a>Parametry szablonu niestandardowego  
 Można określić własne parametry szablonu i wartości, oprócz parametrów zastrzeżonego szablonu domyślnego, które są używane podczas wymiany parametru. Aby uzyskać więcej informacji, zobacz [customparameters — Element (szablony Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md)  
  
## <a name="example-replacing-files-names"></a>Przykład: Zamienianie nazwy plików  
 Nazwy zmiennych plików dla elementów projektu można określić przy użyciu parametru za pomocą atrybutu `TargetFileName`. Na przykład, można określić, że plik .exe użyje nazwy projektu, określonej przez `$projectname$`, jako nazwę pliku.  
  
```  
<TemplateContent>  
    <ProjectItem  
        ReplaceParameters="true"  
        TargetFileName="$projectname$.exe">  
            File1.exe  
    </ProjectItem>  
      ...  
</TemplateContent>  
```  
  
## <a name="example-using-the-project-name-for-the-namespace-name"></a>Przykład: Używanie nazwy projektu dla nazwy przestrzeni nazw  
 Aby użyć nazwy projektu dla przestrzeni nazw w pliku klasy Visual C#, Class1.cs, należy użyć następującej składni:  
  
```  
#region Using directives  
  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
#endregion  
  
namespace $safeprojectname$  
{  
    public class Class1  
        {  
            public Class1()  
                {  
  
                }  
         }  
}  
```  
  
 W pliku .vstemplate dla szablonu projektu należy uwzględnić następujący kod XML podczas odwołania się do pliku Class1.cs:  
  
```  
<TemplateContent>  
    <ProjectItem ReplaceParameters="true">  
        Class1.cs  
    </ProjectItem>  
    ...  
</TemplateContent>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)
