---
title: Debugowanie rozwiązań SharePoint | Dokumentacja firmy Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.WebConfigModificationDialog
- VS.SharePointTools.Project.DebuggingNotEnabled
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, debugging
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cffed1a3905ca1a1aceb9d2cfdcf4abc89f83574
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60060803"
---
# <a name="debug-sharepoint-solutions"></a>Debugowanie rozwiązań SharePoint
  Można debugować rozwiązania programu SharePoint przy użyciu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debugera. Podczas uruchamiania debugowania, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] wdraża pliki projektu na serwerze programu SharePoint, a następnie powoduje otwarcie witryny programu SharePoint w przeglądarce sieci Web. W poniższych sekcjach opisano sposób debugowania aplikacji programu SharePoint w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

- [Włącz debugowanie](#enable-debugging)

- [Proces debugowania, jak i wdrożenie F5](#f5-debug-and-deployment-process)

- [Funkcji projektu SharePoint](#sharepoint-project-features)

- [Debugowanie przepływów pracy](#debug-workflows)

- [Debugowanie funkcji odbiorcy zdarzeń](#debug-feature-event-receivers)

- [Włącz ehanced informacje o debugowaniu](#enable-enhanced-debugging-information)

## <a name="enable-debugging"></a>Włączanie debugowania
 Kiedy najpierw debugować rozwiązania programu SharePoint w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], okno dialogowe ostrzega, że plik web.config nie jest skonfigurowana by włączyć debugowanie. (Plik web.config jest tworzony podczas instalacji serwera programu SharePoint. Aby uzyskać więcej informacji, zobacz [Praca z plikami Web.config](http://go.microsoft.com/fwlink/?LinkID=149266).) Okno dialogowe zapewnia możliwość włączenia debugowania działających projekt bez debugowania lub zmodyfikowanie pliku web.config. Wybranie opcji pierwszy projekt działa normalnie. Jeśli zdecydujesz się druga opcja, plik web.config jest skonfigurowany do:

- Włącz na stosie wywołań (`CallStack="true"`)

- Wyłączanie błędów niestandardowych w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (`<customErrors mode="Off" />`)

- Włącz debugowanie kompilacji (`<compilation debug="true">`)

  Wynikowy plik web.config jest następujący:

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <configuration>
        ...
        <SharePoint>
            <SafeMode MaxControls="200"
                CallStack="true"
                DirectFileDependencies="10"
                TotalFileDependencies="50"
                AllowPageLevelTrace="false">
                ...
            </SafeMode>
        ...
        </SharePoint>
        <system.web>
            ...
            <customErrors mode="Off" />
            ...
            <compilation debug="true">
            ...
            </compilation>
            ...
        </system.web>
        ...
    </configuration>
```

 Aby wycofać zmiany i wyłączyć debugowanie, Zmień następujące [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] w pliku web.config:

- Wyłącz stos wywołań (`CallStack="false"`)

- Włącz błędy niestandardowe w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (`<customErrors mode="On" />`)

- Należy wyłączyć debugowanie kompilacji (`<compilation debug="false">`)

## <a name="f5-debug-and-deployment-process"></a>Proces debugowania, jak i wdrożenie F5
 Po uruchomieniu projektu programu SharePoint w trybie debugowania procesu wdrażania programu SharePoint wykonuje następujące zadania:

1. Uruchamia polecenia przed wdrożeniem można dostosowywać.

2. Tworzy plik pakietu (wsp) przy użyciu rozwiązań sieci Web przy użyciu [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] poleceń. Plik .wsp obejmuje wszystkie niezbędne pliki i funkcje. Aby uzyskać więcej informacji, zobacz [omówienie rozwiązań](http://go.microsoft.com/fwlink/?LinkID=128154).

3. Rozwiązania programu SharePoint jest rozwiązanie farmy, jest odtwarzana [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] pulę aplikacji dla określonej lokacji [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]. W tym kroku zwalnia pliki zablokowane przez [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] procesu roboczego.

4. Jeśli poprzednią wersję pakietu już istnieje, wycofująca poprzednią wersję funkcji i plików w pliku wsp. W tym kroku dezaktywuje funkcji, odinstalowuje pakiet rozwiązania, a następnie usuwa pakietu rozwiązania na serwerze programu SharePoint.

5. Instaluje bieżącej wersji funkcji i plików w pliku wsp. Ten krok dodaje i instaluje rozwiązanie na serwerze programu SharePoint.

6. W przypadku przepływów pracy instaluje zestawu przepływu pracy. Można zmienić lokalizacji za pomocą *lokalizacji zestawu* właściwości.

7. Aktywuje funkcję projektu w programie SharePoint, jeśli zakres jest lokacji lub w sieci Web. Funkcje w zakresach farmy i aplikacji sieci Web nie są uaktywnione.

8. W przypadku przepływów pracy, skojarzenie przepływu pracy z biblioteki programu SharePoint, listy lub witryny, które wybrano w **Kreator ustawień niestandardowych SharePoint**.

   > [!NOTE]
   >  To skojarzenie występuje tylko wtedy, gdy wybrano **automatyczne kojarzenie przepływu pracy** w kreatorze.

9. Uruchamia polecenia po wdrożeniu można dostosowywać.

10. Dołącza [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debuger [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] procesu (*w3wp.exe*). Jeśli typ projektu pozwala zmienić *rozwiązanie w trybie piaskownicy* właściwości i jej wartość jest równa **true**, debuger dołącza do innego procesu, a następnie (*SPUCWorkerProcess.exe*). Aby uzyskać więcej informacji, zobacz [uwagi dotyczące rozwiązania typu piaskownica](../sharepoint/sandboxed-solution-considerations.md).

11. Uruchamia debuger JavaScript, jeśli rozwiązanie programu SharePoint jest rozwiązanie farmy.

12. Wyświetla odpowiednią bibliotekę, listy lub strony witryny w przeglądarce sieci Web.

    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Wyświetla komunikat o stanie w oknie danych wyjściowych, po zakończeniu każdego zadania. Jeśli nie można ukończyć zadania, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] wyświetla komunikat o błędzie w oknie Lista błędów.

## <a name="sharepoint-project-features"></a>Funkcji projektu SharePoint
 Funkcja jest jednostką przenośny i modularnej funkcji, które upraszcza modyfikacja lokacji przy użyciu definicji witryny. Warto również pakiet [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] elementów (WSS), może być aktywowana dla określonego zakresu i która pomaga użytkownikom wykonania konkretnego celu lub zadania. Szablony są wdrażane jako funkcje.

 Kiedy uruchamiasz projekt w trybie debugowania, proces wdrażania tworzy folder w *funkcji* katalogu na *%COMMONPROGRAMFILES%\Microsoft Shared\web server extensions\14\TEMPLATE\FEATURES*. Nazwy funkcji mają format *Nazwa projektu*_funkcji*x*, takich jak TestProject_Feature1.

 Folder rozwiązania w katalogu funkcji zawiera *definicji funkcji* pliku i *definicji przepływu pracy* pliku. Plik definicji funkcji (Feature.xml) opisano pliki w pliku definicji projektu Feature.The projektu (*Elements.xml*) opisuje szablon projektu. *Elements.XML* znajdują się w **Eksploratora rozwiązań**, ale Feature.xml jest generowany po utworzeniu pakietu rozwiązania. Aby uzyskać więcej informacji o tych plikach, zobacz [SharePoint szablony elementu projektu i projektu](../sharepoint/sharepoint-project-and-project-item-templates.md).

## <a name="debug-workflows"></a>Debugowania przepływów pracy
 Podczas debugowania projektów przepływu pracy [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje szablon przepływu pracy (w zależności od typu), do biblioteki lub listy. Następnie należy uruchomić szablonu przepływu pracy, ręcznie lub przez dodanie lub zaktualizowanie elementu. Następnie można użyć [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debugowanie przepływu pracy.

> [!NOTE]
>  Po dodaniu odwołania do innych zestawów, upewnij się, że te zestawy są zainstalowane w globalnej pamięci podręcznej ( [!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]). W przeciwnym razie rozwiązaniu przepływ pracy zakończy się niepowodzeniem. Aby uzyskać informacje o sposobie instalowania zestawów, zobacz [ręcznie uruchomić przepływ pracy dla dokumentu lub elementu](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963).

 Jednak proces wdrażania nie można uruchomić przepływu pracy. W witrynie sieci Web programu SharePoint, należy uruchomić przepływ pracy. Można również uruchomić przepływ pracy za pomocą aplikacji klienckiej, takich jak Microsoft Office Word 2010 lub przy użyciu osobnego kodu po stronie serwera. Użyj jednej z metod, określone w **Kreator ustawień niestandardowych SharePoint**.

 Na przykład jeśli określono, że przepływ pracy może zostać uruchomione ręcznie, należy uruchomić przepływ pracy bezpośrednio z elementu w bibliotece lub na liście. Aby uzyskać więcej informacji o tym, jak ręcznie uruchomić przepływ pracy, zobacz [ręcznie uruchomić przepływ pracy element dokumentu](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963).

## <a name="debug-feature-event-receivers"></a>Debugowanie funkcji odbiorcy zdarzeń
 Domyślnie po uruchomieniu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aplikacji programu SharePoint, jej funkcje zostaną automatycznie aktywowane automatycznie na serwerze programu SharePoint. Jednak powoduje to problemy podczas debugowania funkcji zdarzenia odbiorców, ponieważ gdy funkcja jest aktywowana za [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], działa w ramach innego procesu niż debugera. Oznacza to, że niektóre funkcje debugowania, takie jak punkty kontrolne, nie będą działać poprawnie.

 Aby wyłączyć automatyczną aktywację funkcji w programie SharePoint i zezwolenia na debugowanie właściwe dla funkcji odbiorcy zdarzeń, ustaw wartość projektu **aktywnej konfiguracji wdrożenia** właściwość **aktywacji nie** przed debugowaniem. Następnie, po rozpoczęciu debugowania aplikacji programu SharePoint w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], ręcznie aktywować tej funkcji w programie SharePoint. Aby aktywować tę funkcję, otwórz **Akcje witryny** menu w programie SharePoint, wybierz opcję **ustawienia lokacji**, wybierz **Zarządzanie funkcji witryny** łącze, a następnie wybierz **Aktywuj** przycisk obok funkcji, aby kontynuować debugowanie w zwykły sposób.

## <a name="enable-enhanced-debugging-information"></a>Włącz rozszerzone informacje o debugowaniu
 Z powodu czasami złożone interakcje między [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] procesu (devenv.exe) [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] procesie hosta programu SharePoint (*vssphost4.exe*), SharePoint i warstwę WCF diagnozowanie błędów występujących podczas Tworzenie, wdrażanie i tak dalej, może być trudne. Aby pomóc Ci rozwiązać błędy takie, można włączyć rozszerzone informacje o debugowaniu. Aby to zrobić, przejdź do następującego klucza rejestru w rejestrze systemu Windows:

 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools**

 Jeśli "EnableDiagnostics" **REG_DWORD** wartość jeszcze nie istnieje, utworzenie go ręcznie. Ustaw wartość "EnableDiagnostics" na "1".

 Ustawienie tej wartości klucza 1 powoduje, że stos śledzenia informacji do wyświetlania w **dane wyjściowe** okna zawsze wtedy, gdy projekt systemu błędy występują, gdy są uruchomione [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Aby wyłączyć rozszerzone informacje o debugowaniu, wartość EnableDiagnostics 0 lub usunąć wartości.

 Aby uzyskać więcej informacji na temat kluczy rejestru programu SharePoint, zobacz [Debugowanie rozszerzeń dla narzędzi SharePoint w programie Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Zobacz także
- [Rozwiązywanie problemów z rozwiązaniami SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md)
