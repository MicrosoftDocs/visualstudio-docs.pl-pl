---
title: 'Instrukcje: Tworzenie szablonów elementu | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- project item templates, XML reference
- project item templates, custom template locations
- project item templates, creating
- project item templates, metadata files
ms.assetid: 77bc53d4-d607-4820-a032-7e3b365891b5
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4484ec75cf44fc60c72091fb17cce510efdb9cd4
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63417023"
---
# <a name="how-to-create-item-templates"></a>Instrukcje: Tworzenie szablonów elementu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kroki opisane w [pierwszej procedury](#to-add-a-custom-project-item-template-to-the-add-new-item-dialog-box) części tego tematu dowiesz się, jak utworzyć szablon elementu za pomocą **Eksportuj szablon** kreatora. Jeśli Twój szablon będzie składać się z wielu plików, zobacz [jak: Tworzenie szablonów elementów wielu plików](../ide/how-to-create-multi-file-item-templates.md).  
  
 Kreator sporego nakładu pracy w celu utworzenia podstawowego szablonu, ale w wielu przypadkach należy ręcznie zmodyfikować plik .vstemplate po wyeksportowaniu szablonu. Na przykład, jeśli chcesz, aby element był wyświetlany w **Dodaj nowy element** okno dialogowe [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] projekt aplikacji należy wykonać kilka dodatkowych kroków. [Druga procedura](#to-enable-the-item-template-to-be-used-in-a-store-project) w tym temacie pomaga wykonać to zadanie.  
 
 W niektórych przypadkach może być ma lub należy ręcznie utworzyć szablon elementu od podstaw. [Trzeci procedury](#to-enable-templates-for-specific-project-sub-types) pokazuje, jak to zrobić.  
  
 Zobacz [odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md) uzyskać informacji na temat elementów, które mogą być używane w pliku .vstemplate.  
  
### <a name="to-add-a-custom-project-item-template-to-the-add-new-item-dialog-box"></a>Aby dodać szablon elementu niestandardowego projektu do okna dialogowego Dodaj nowy element  
  
1. Utwórz lub Otwórz projekt w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
2. Dodaj element do projektu i zmodyfikuj go, jeśli chcesz.  
  
3. Zmodyfikuj plik kodu, aby wskazać, gdzie wymiany parametru powinny zostać wykonane. Aby uzyskać więcej informacji, zobacz [jak: Zastępowanie parametrów w szablonie](../ide/how-to-substitute-parameters-in-a-template.md).  
  
4. Na **pliku** menu, kliknij przycisk **Eksportuj szablon**.  
  
5. Kliknij przycisk **szablon elementu**, a następnie wybierz projekt, który zawiera element i kliknij przycisk **dalej**.  
  
6. Wybierz element, dla którego chcesz utworzyć szablon, a następnie kliknij przycisk **dalej**.  
  
7. Wybierz odwołania do zestawu do uwzględnienia w szablonie, a następnie kliknij przycisk **dalej**.  
  
8. Wpisz nazwę pliku ikony, obraz podglądu, nazwę szablonu i opis szablonu, a następnie kliknij przycisk **Zakończ**.  
  
     Pliki szablonu są dodawane do pliku .zip i kopiowane do katalogu, niezależnie od określonej w oknie dialogowym. Domyślna lokalizacja to **... \Users\\< nazwa_użytkownika\>\Documents\Visual Studio \<wersji > \My wyeksportowane szablony\\**  folderu.  
  
    > [!WARNING]
    > We wcześniejszych wersjach programu Visual Studio, domyślna lokalizacja to **... \Users\\< nazwa_użytkownika\>\Documents\Visual Studio \<wersji > \Templates\ItemTemplates**.  
  
### <a name="to-enable-the-item-template-to-be-used-in-a-store-project"></a>Aby włączyć szablon elementu, który ma być używany w projekcie magazynu  
  
1. Postępuj zgodnie z instrukcjami w poprzedniej procedurze, aby wyeksportować szablon elementu.  
  
2. Wyodrębnij plik .vstemplate z pliku .zip, skopiowanego do.. \Users\\*username*\Documents\Visual Studio *wersji*\Templates\ItemTemplates\ (lub **Moje szablony wyeksportowane**) folder.  
  
3. Otwórz plik .vstemplate w programie Visual Studio.  
  
4. Windows 8.1 przechowywania projektu C# w pliku .vstemplate, Dodaj następujący kod XML między otwierającym i zamykającym `<TemplateData>` tagu: `<TemplateGroupID>WinRT-Managed</TemplateGroupID>`.  
  
    Projekt ze Sklepu Windows 8.1 C++ używa wartości `WinRT-Native-6.3`. Windows 10 i innych typów projektów, zobacz [templategroupid — Element (szablony Visual Studio)](../extensibility/templategroupid-element-visual-studio-templates.md).  
  
    W poniższym przykładzie pokazano całą zawartość pliku .vstemplate po wierszu kodu XML `<TemplateGroupID>WinRT-Managed</TemplateGroupID>` dodano do niego. W tym przykładzie jest specyficzne dla projektów języka C#. Możesz zmodyfikować \<ProjectType > i \< [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)> elementy, aby określić inne typy języka i projektu.  
  
   ```xml  
   <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">  
     <TemplateData>  
       <DefaultName>MyItemStoreTemplate.xaml</DefaultName>  
       <Name>MyItemStoreTemplate</Name>  
       <Description>This is an example itemtemplate</Description>  
       <ProjectType>CSharp</ProjectType>  
       <SortOrder>10</SortOrder>  
       <Icon>__TemplateIcon.ico</Icon>  
       <TemplateGroupID>WinRT-Managed</TemplateGroupID>  
     </TemplateData>  
     <TemplateContent>  
       <References />  
       <ProjectItem SubType="Designer" TargetFileName="$fileinputname$.xaml" ReplaceParameters="true">MyItemTemplate.xaml</ProjectItem>  
       <ProjectItem SubType="Code" TargetFileName="$fileinputname$.xaml.cs" ReplaceParameters="true">MyItemTemplate.xaml.cs</ProjectItem>  
     </TemplateContent>  
   </VSTemplate>  
   ```  
  
    Aby uzyskać inne możliwe wartości TemplateGroupID, zobacz [templategroupid — Element (szablony Visual Studio)](../extensibility/templategroupid-element-visual-studio-templates.md)). Aby .vstemplate pełne informacje, zobacz [odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)  
  
5. W programie Visual Studio Zapisz plik .vstemplate i zamknij go.  
  
6. Skopiuj i wklej plik .vstemplate z powrotem do pliku zip, znajduje się w.. \Users\\*username*\Documents\Visual Studio *wersji*\Templates\ItemTemplates\ folderu.  
  
    Jeśli **kopiowania pliku** pojawi się okno dialogowe, wybierz **Kopiuj i Zamień** opcji.  
  
   Możesz teraz dodać element na podstawie tego szablonu do [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] projektu przy użyciu **Dodaj nowy element** okno dialogowe.  
  
   Aby uzyskać więcej informacji na temat nazw parametrów, zobacz [parametry szablonu](../ide/template-parameters.md).  
  
### <a name="to-enable-templates-for-specific-project-sub-types"></a>Aby umożliwić szablony dla określonego projektu podtypów  
  
1. Środowisko projektowe pozwala udostępnić elementy projektu w oknie dialogowym Dodawanie elementu dla niektórych projektów. Użyj tej procedury, aby udostępnić niestandardowe elementy Windows, sieci Web, pakietu Office i projekty bazy danych.  
  
    Znajdź ProjectType element w pliku .vstemplate szablonu elementu.  
  
    Dodaj [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) element natychmiast po PROJECTTYPE — element.  
  
2. Ustaw wartość tekstowego elementu do jednego z następujących wartości:  
  
   1. Windows  
  
   2. Office  
  
   3. Baza danych  
  
   4. sieć Web  
  
      Na przykład: `<ProjectSubType>Database</ProjectSubType>`.  
  
      Poniższy przykład przedstawia szablon elementu dostępne dla projektów pakietu Office.  
  
   ```  
   <VSTemplate Version="2.0.0" Type="Item" Version="2.0.0">  
       <TemplateData>  
           <Name>Class</Name>  
           <Description>An empty class file</Description>  
           <Icon>Class.ico</Icon>  
           <ProjectType>CSharp</ProjectType>  
           <ProjectSubType>Office</ProjectSubType>  
           <DefaultName>Class.cs</DefaultName>  
       </TemplateData>  
       <TemplateContent>  
           <ProjectItem>Class1.cs</ProjectItem>  
       </TemplateContent>  
   </VSTemplate>  
  
   ```  
  
### <a name="to-manually-create-an-item-template-without-using-the-export-template-wizard"></a>Aby ręcznie utworzyć szablon elementu bez użycia Kreatora eksportowania szablonu  
  
1. Tworzenie projektu i elementu projektu.  
  
2. Zmodyfikuj element projektu, dopóki nie jest gotowa do zapisania jako szablonu.  
  
3. Zgodnie z potrzebami zmodyfikuj plik kodu, aby wskazać, gdzie powinno nastąpić wymiany parametru. Aby uzyskać więcej informacji na temat wymiany parametru Zobacz jak: Zastępowanie parametrów w szablonie.  
  
4. Utwórz plik XML i zapisz go przy użyciu rozszerzenia nazwy pliku .vstemplate, w tym samym katalogu, co Twój nowy szablon elementu.  
  
5. Tworzenie pliku XML .vstemplate do udostępnienia metadanych szablonu elementu. Aby uzyskać więcej informacji, zobacz [odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md) i w przykładzie w poprzedniej sekcji.  
  
6. Zapisz plik .vstemplate i zamknij go.  
  
7. W Eksploratorze Windows wybierz pliki, które chcesz uwzględnić w szablonie, kliknij prawym przyciskiem myszy zaznaczenie, kliknij przycisk Wyślij do, a następnie kliknij Folder skompresowany (zip). Wybrane pliki są kompresowane w pliku zip.  
  
8. Skopiuj plik zip i wklej go w lokalizacji szablonów elementów użytkownika. W programie Visual Studio 2015 domyślnym katalogiem jest... \Users\\< nazwa_użytkownika\>\Documents\Visual Studio 2015\Templates\ItemTemplates\\. Aby uzyskać więcej informacji, zobacz jak: Znajdź i organizowania projektów i szablonów elementów.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)   
 [Instrukcje: Tworzenie szablonów elementów wielu plików](../ide/how-to-create-multi-file-item-templates.md)   
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
