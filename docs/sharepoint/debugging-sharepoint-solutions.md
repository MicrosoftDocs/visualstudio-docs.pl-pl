---
title: Debugowanie rozwiązań programu SharePoint | Microsoft Docs
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
ms.openlocfilehash: d83c8ffd4fe5ebb627b70fa07f010bdc713225dd
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984488"
---
# <a name="debug-sharepoint-solutions"></a>Debuguj rozwiązania programu SharePoint
  Można debugować rozwiązania programu SharePoint za pomocą debugera [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Po rozpoczęciu debugowania program [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] wdraża pliki projektu na serwerze programu SharePoint, a następnie otwiera wystąpienie witryny programu SharePoint w przeglądarce sieci Web. W poniższych sekcjach wyjaśniono, jak debugować aplikacje programu SharePoint w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

- [Włącz debugowanie](#enable-debugging)

- [Debugowanie i proces wdrażania w F5](#f5-debug-and-deployment-process)

- [Funkcje projektu programu SharePoint](#sharepoint-project-features)

- [Debuguj przepływy pracy](#debug-workflows)

- [Odbiorniki zdarzeń funkcji debugowania](#debug-feature-event-receivers)

- [Włącz informacje o debugowaniu ehanced](#enable-enhanced-debugging-information)

## <a name="enable-debugging"></a>Włączanie debugowania
 Podczas pierwszego debugowania rozwiązania programu SharePoint w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]okno dialogowe ostrzega o tym, że plik Web. config nie jest skonfigurowany do włączania debugowania. (Plik Web. config jest tworzony podczas instalowania programu SharePoint Server. Aby uzyskać więcej informacji, zobacz [Praca z plikami Web. config](/previous-versions/office/developer/sharepoint-2010/ms460914(v=office.14)). To okno dialogowe umożliwia uruchomienie projektu bez debugowania lub modyfikacji pliku Web. config w celu włączenia debugowania. W przypadku wybrania pierwszej opcji projekt jest uruchamiany normalnie. W przypadku wybrania drugiej opcji plik Web. config jest skonfigurowany do:

- Włącz stos wywołań (`CallStack="true"`)

- Wyłącz błędy niestandardowe w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (`<customErrors mode="Off" />`)

- Włącz debugowanie kompilacji (`<compilation debug="true">`)

  Utworzony plik Web. config jest następujący:

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

 Aby wycofać zmiany i wyłączyć debugowanie, należy zmienić następujące [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] w pliku Web. config:

- Wyłącz stos wywołań (`CallStack="false"`)

- Włącz błędy niestandardowe w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (`<customErrors mode="On" />`)

- Wyłącz debugowanie kompilacji (`<compilation debug="false">`)

## <a name="f5-debug-and-deployment-process"></a>Debugowanie i proces wdrażania w F5
 Po uruchomieniu projektu programu SharePoint w trybie debugowania proces wdrażania programu SharePoint wykonuje następujące zadania:

1. Uruchamia dostosowywalne polecenia przed wdrożeniem.

2. Tworzy plik pakietu rozwiązania sieci Web (wsp) za pomocą poleceń [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]. Plik. wsp zawiera wszystkie niezbędne pliki i funkcje. Aby uzyskać więcej informacji, zobacz [Omówienie rozwiązań](/previous-versions/office/developer/sharepoint-2010/aa543214(v=office.14)).

3. Jeśli rozwiązanie SharePoint jest rozwiązaniem farmy, odtwarza [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] pulę aplikacji dla określonej lokacji [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]. Ten krok zwalnia pliki zablokowane przez proces roboczy [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)].

4. Jeśli poprzednia wersja pakietu już istnieje, wycofuje poprzednią wersję funkcji i plików w pliku wsp. Ten krok powoduje dezaktywację funkcji, odinstalowanie pakietu rozwiązania, a następnie usunięcie pakietu rozwiązania na serwerze programu SharePoint.

5. Instaluje bieżącą wersję funkcji i plików w pliku. wsp. Ten krok powoduje dodanie i zainstalowanie rozwiązania na serwerze programu SharePoint.

6. W przypadku przepływów pracy program instaluje zestaw przepływu pracy. Swoją lokalizację można zmienić przy użyciu właściwości *Lokalizacja zestawu* .

7. Aktywuje funkcję projektu w programie SharePoint, jeśli zakresem jest lokacja lub sieć Web. Funkcje w farmie i zakresach aplikacji internetowej nie są aktywowane.

8. W przypadku przepływów pracy program kojarzy przepływ pracy z biblioteką programu SharePoint, listą lub witryną wybraną w **Kreatorze dostosowywania programu SharePoint**.

   > [!NOTE]
   > To skojarzenie odbywa się tylko w przypadku wybrania w kreatorze **automatycznego skojarzenia przepływu pracy** .

9. Uruchamia dostosowywalne polecenia po wdrożeniu.

10. Dołącza debuger [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] do procesu [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (*w3wp. exe*). Jeśli typ projektu pozwala zmienić właściwość *rozwiązania w trybie piaskownicy* , a jej wartość jest równa **true**, debuger dołącza do innego procesu (*SPUCWorkerProcess. exe*). Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące rozwiązania w trybie piaskownicy](../sharepoint/sandboxed-solution-considerations.md).

11. Uruchamia debuger JavaScript, jeśli rozwiązanie SharePoint jest rozwiązaniem farmy.

12. Wyświetla odpowiednią bibliotekę, listę lub stronę witryny w przeglądarce sieci Web.

    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] wyświetla komunikat o stanie w oknie danych wyjściowych po zakończeniu każdego zadania. Jeśli zadanie nie może zostać ukończone, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] wyświetli komunikat o błędzie w oknie Lista błędów.

## <a name="sharepoint-project-features"></a>Funkcje projektu programu SharePoint
 Funkcja jest przenośną i modularną jednostką funkcji, która upraszcza modyfikację lokacji przy użyciu definicji lokacji. Jest to również pakiet elementów [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS), które można uaktywnić dla określonego zakresu, aby ułatwić użytkownikom wykonywanie określonych celów lub zadań. Szablony są wdrażane jako funkcje.

 Po uruchomieniu projektu w trybie debugowania proces wdrażania tworzy folder w katalogu *funkcji* na *%CommonProgramFiles%\Microsoft Shared\Web Server extensions\14\TEMPLATE\FEATURES*. Nazwy funkcji mają format *nazwy projektu*_Feature*x*, taki jak TestProject_Feature1.

 Folder rozwiązania w katalogu funkcji zawiera plik *definicji funkcji* i plik *definicji przepływu pracy* . Plik definicji funkcji (feature. xml) zawiera opis plików w funkcji projektu. plik definicji projektu (*elementy. XML*) zawiera opis szablonu projektu. *Elementy. XML* można znaleźć w **Eksplorator rozwiązań**, ale funkcja feature. XML jest generowana podczas tworzenia pakietu rozwiązania. Aby uzyskać więcej informacji o tych plikach, zobacz [Szablony projektów i elementów projektu programu SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).

## <a name="debug-workflows"></a>Debugowania przepływów pracy
 Podczas debugowania projektów przepływu pracy [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje szablon przepływu pracy (w zależności od jego typu) do biblioteki lub listy. Następnie można uruchomić szablon przepływu pracy ręcznie lub przez dodanie lub zaktualizowanie elementu. Następnie można użyć [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] do debugowania przepływu pracy.

> [!NOTE]
> W przypadku dodawania odwołań do innych zestawów upewnij się, że te zestawy są zainstalowane w globalnej pamięci podręcznej zestawów ([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]). W przeciwnym razie rozwiązanie przepływu pracy zakończy się niepowodzeniem. Informacje o sposobach instalowania zestawów znajdują się w temacie [Ręczne uruchamianie przepływu pracy dla dokumentu lub elementu](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963).

 Jednak proces wdrażania nie powoduje uruchomienia przepływu pracy. Przepływ pracy należy uruchomić z witryny sieci Web programu SharePoint. Przepływ pracy można również uruchomić przy użyciu aplikacji klienckiej, takiej jak Microsoft Office Word 2010 lub przy użyciu osobnego kodu po stronie serwera. Użyj jednego z metod określonych w **Kreatorze dostosowania programu SharePoint**.

 Na przykład jeśli określono, że przepływ pracy można uruchomić ręcznie, należy uruchomić przepływ pracy bezpośrednio z poziomu elementu w bibliotece lub liście. Aby uzyskać więcej informacji na temat ręcznego uruchamiania przepływu pracy, zobacz [Ręczne uruchamianie przepływu pracy w elemencie dokumentu](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963).

## <a name="debug-feature-event-receivers"></a>Odbiorniki zdarzeń funkcji debugowania
 Domyślnie po uruchomieniu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aplikacji programu SharePoint jej funkcje są automatycznie uaktywniane na serwerze programu SharePoint. Powoduje to jednak problemy podczas debugowania odbiorników zdarzeń funkcji, ponieważ funkcja jest aktywowana przez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], działa w innym procesie niż debuger. Oznacza to, że niektóre funkcje debugowania, takie jak punkty przerwania, nie będą działać poprawnie.

 Aby wyłączyć automatyczną aktywację funkcji w programie SharePoint i zezwolić na prawidłowe debugowanie odbiorników zdarzeń funkcji, należy ustawić wartość właściwości **Konfiguracja aktywnego wdrożenia** projektu na **Brak aktywacji** przed debugowaniem. Następnie po rozpoczęciu debugowania aplikacji programu SharePoint w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]ręcznie Aktywuj tę funkcję w programie SharePoint. Aby aktywować tę funkcję, otwórz menu **Akcje witryny** w programie SharePoint, wybierz pozycję **Ustawienia witryny**, wybierz łącze **Zarządzaj funkcjami lokacji** , a następnie wybierz przycisk **Aktywuj** obok funkcji, aby kontynuować debugowanie jako normalne.

## <a name="enable-enhanced-debugging-information"></a>Włącz rozszerzone informacje o debugowaniu
 Ze względu na czasami złożone interakcje między procesem [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (devenv. exe), [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] procesie hosta programu SharePoint (*vssphost4. exe*), SharePoint i warstwą WCF, Diagnozowanie błędów występujących podczas kompilowania, wdrażania i tak dalej może być Sprawdz. Aby ułatwić rozwiązanie takich błędów, można włączyć ulepszone informacje o debugowaniu. W tym celu przejdź do następującego klucza rejestru w rejestrze systemu Windows:

 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools**

 Jeśli wartość **parametru REG_DWORD** "EnableDiagnostics" jeszcze nie istnieje, utwórz ją ręcznie. Ustaw wartość "EnableDiagnostics" na "1".

 Ustawienie tej wartości klucza na 1 powoduje, że informacje o śledzeniu stosu pojawiają się w oknie **danych wyjściowych** za każdym razem, gdy program jest uruchomiony w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Aby wyłączyć ulepszone informacje o debugowaniu, ustaw EnableDiagnostics z powrotem na 0 lub usuń wartość.

 Aby uzyskać więcej informacji na temat innych kluczy rejestru programu SharePoint, zobacz [Debugowanie rozszerzeń dla narzędzi programu SharePoint w programie Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Zobacz także
- [Rozwiązywanie problemów z rozwiązaniami programu SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md)
