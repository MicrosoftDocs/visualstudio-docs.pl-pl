---
title: Pakowanie i wdrażanie rozwiązań programu SharePoint | Dokumentacja firmy Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- packaging [SharePoint development in Visual Studio]
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, packaging and deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a50d7088cdeb868ef4170e3b4b76fbf129151626
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54867640"
---
# <a name="package-and-deploy-sharepoint-solutions"></a>Pakowanie i wdrażanie rozwiązań SharePoint
  Zwykle rozwiązania programu SharePoint jest wdrażana na serwerze programu SharePoint przy użyciu pliku pakietu (wsp) rozwiązania. Można użyć programu Visual Studio, aby organizowanie elementów projektu programu SharePoint w funkcji i utworzyć pakiet do wdrożenia funkcji programu SharePoint.  
  
 Ten temat zawiera następujące informacje:  
  
-   [Tworzenie pakietów i funkcji](#Creating)  
  
-   [Funkcja i pakowanie, narzędzie pomocy technicznej](#Tools)  
  
-   [Wdrażanie rozwiązań programu SharePoint](#Deploying)  
  
-   [Wdrażanie plików w rozwiązaniach programu SharePoint](#DeployingFiles)  
  
## <a name="create-features-and-packages"></a>Tworzenie pakietów i funkcji
 Używasz programu Visual Studio do grupowania powiązanych elementów programu SharePoint do *funkcji*. Na przykład funkcję dla definicji listy kontaktów może obejmować wystąpienie listy i definicji listy. Te dwa elementy można łączyć w pojedynczej funkcji do celów wdrożenia. Aby uzyskać więcej informacji o funkcjach, zobacz [bloków konstrukcyjnych: Funkcje](http://go.microsoft.com/fwlink/?LinkID=169183).  
  
 Następnie można utworzyć pakietu rozwiązania programu SharePoint (*.wsp*) do połączenia wielu funkcji, lokacji w jeden pakiet, który przechowuje pliki w formacie wymagane przez program SharePoint do wdrożenia pliki do definicji, zespoły i inne pliki serwer. Aby uzyskać więcej informacji, zobacz [bloków konstrukcyjnych: Rozwiązania](http://go.microsoft.com/fwlink/?LinkID=169186).  
  
## <a name="feature-and-packaging-tool-support"></a>Funkcja i Obsługa narzędzia pakowania
 Narzędzia programistyczne programu SharePoint w programie Visual Studio umożliwia szybkie organizowanie plików programu SharePoint do funkcji i pakietów rozwiązań ułatwia wdrożenia. Aby skonfigurować pakiet funkcji i rozwiązania, można użyć następujących narzędzi.  
  
-   Projektant funkcji i projektancie pakietu.  
  
-   Eksploratora pakietów jest oknem narzędzi.  
  
-   Eksplorator rozwiązań.  
  
### <a name="feature-designer-and-package-designer"></a>Funkcja projektanta i projektanta pakietów
 Możesz tworzyć funkcje, ustaw zakresy i inne funkcje należy oznaczyć jako zależności za pomocą projektanta funkcji. Projektant wyświetla również końcowego pliku XML, który opisuje każdej funkcji. Aby uzyskać więcej informacji, zobacz [funkcji SharePoint Utwórz](../sharepoint/creating-sharepoint-features.md).  
  
 Zastosuj tę funkcję z określonej witryny sieci Web lub grupą witryn sieci Web, ustawiając jego *zakres* w Projektancie funkcji. Jeśli funkcja jest aktywowana dla poszczególnych witryn sieci Web, ta funkcja działa tylko w tej konkretnej witryny sieci Web. Jeśli funkcja jest aktywowana dla zbioru witryn, elementy w funkcji są stosowane do kolekcji w całej lokacji. Aby uzyskać więcej informacji, zobacz [zakres elementu](http://go.microsoft.com/fwlink/?LinkID=169189).  
  
 Jeśli Twoja funkcja opiera się na inne funkcje, możesz ustawić *zależność aktywacji funkcji* do oznaczenia funkcji zależnych przed udostępnieniem Twojej funkcji. Zależność aktywacji funkcji kontroli, jeśli funkcje zależne są już aktywowane w tym zakresie. Aby uzyskać więcej informacji, zobacz [zależności aktywacji i zakres](http://go.microsoft.com/fwlink/?LinkID=169190).  
  
 W Projektancie pakietów można grupować elementy programu SharePoint w pakiecie jednego rozwiązania i skonfiguruj opcję Resetuj serwer sieci Web podczas wdrażania. Aby ustawić typ serwera wdrożenia, użyj **właściwości** okna. Projektant generuje również plik XML, który opisuje zawartość pakietu. Aby uzyskać więcej informacji, zobacz [pakietów rozwiązania SharePoint Utwórz](../sharepoint/creating-sharepoint-solution-packages.md).  
  
 Podczas wdrażania usługi Internet Information Services (IIS) jest zatrzymana, można skopiować pliki rozwiązania do serwera programu SharePoint. Przy użyciu projektanta pakietów w programie Visual Studio, możesz wybrać, czy należy ponownie uruchomić serwer sieci Web. Aby skonfigurować, jeśli rozwiązanie jest wdrożone na serwerze frontonu sieci Web lub serwera aplikacji, użyj **właściwości** okna. Aby uzyskać więcej informacji, zobacz [Element rozwiązania (rozwiązanie)](http://go.microsoft.com/fwlink/?LinkID=169191).  
  
### <a name="packaging-explorer"></a>Eksploratora pakietów  
 Jako uzupełnienie funkcji projektanta i projektancie pakietu, można użyć Eksploratora pakietów do grupy plików programu SharePoint do funkcji i pakietów. Ponadto, zobaczysz hierarchiczny widok projektu SharePoint pakietu, funkcje, elementy i pliki. Eksploratora pakietów jest oknem narzędzi, który umożliwia wykonywanie następujących zadań:  
  
- Otwórz elementów projektu programu SharePoint i plików.  
  
- Przeciągnij i upuść elementów projektu programu SharePoint z jedną funkcję.  
  
- Przeciągnij i upuść elementów projektu programu SharePoint i funkcji z jednego pakietu.  
  
- Dodanie nowej funkcji do pakietu.  
  
- Otwórz projektanta funkcji lub pakietów.  
  
- Sprawdź poprawność funkcji i pakietów.  
  
  Narzędzia projektowania programu SharePoint w programie Visual Studio mają reguły sprawdzania poprawności, aby mieć pewność, że pakiet rozwiązania jest poprawnie uformowany. Ponadto zasad upewnij się, że *.wsp* plik rozwiązania można pomyślnie wdrożyć i aktywować na serwerze programu SharePoint. Aby uzyskać więcej informacji na temat schematu XML dla funkcji, zobacz [schematów funkcji](http://go.microsoft.com/fwlink/?LinkID=169192).  
  
  Można dodać funkcji niestandardowej oraz zasady walidacji pakietu do systemu projektu programu SharePoint. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie funkcji niestandardowej oraz pakiet reguł sprawdzania poprawności dla rozwiązań SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).  
  
  Aby uzyskać więcej informacji na temat Eksploratora pakietów, zobacz [jak: Dodawanie i usuwanie funkcji oraz elementów do pakietu przy użyciu Eksploratora pakietów](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).  
  
### <a name="solution-explorer"></a>Eksplorator rozwiązań
 Przejdź do otwierania plików projektu programu SharePoint, można użyć Eksploratora rozwiązań. Użyj menu kontekstowego w Eksploratorze rozwiązań, aby dodać funkcje, funkcji zdarzenia odbiorców, a zasoby funkcji. Ponadto można otworzyć funkcji projektantów i projektanci pakietów, do konfigurowania funkcji oraz pakiety na potrzeby wdrażania.  
  
## <a name="deploy-sharepoint-solutions"></a>Wdrażanie rozwiązań SharePoint
 Po dostosowaniu funkcji i pakietów w programie Visual Studio, można utworzyć *.wsp* plików do wdrożenia na serwerach programu SharePoint. Visual Studio umożliwia debugowanie i testowanie. *wsp* tylko na serwerze programu SharePoint na komputerze deweloperskim. Aby uzyskać więcej informacji na temat wdrażania rozwiązania programu SharePoint na serwerze zdalnym programu SharePoint, zobacz [wdrażanie rozwiązania](http://go.microsoft.com/fwlink/?LinkID=169194).  
  
 Można również dostosować kroki wdrażania na komputerze deweloperskim. Aby uzyskać więcej informacji, zobacz [wdrażanie, publikowanie oraz aktualizowanie pakietów rozwiązania SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).  
  
## <a name="deploy-files-in-sharepoint-solutions"></a>Wdrażanie plików w rozwiązaniach programu SharePoint
 Zazwyczaj podczas dodawania elementu projektu programu SharePoint do rozwiązania programu SharePoint, wszystkie wymagane pliki są uwzględniane. Pliki, które mogą być skompilowane (pliki kodu) są wbudowane w zestawie danych wyjściowych rozwiązania. Jednak również może być konieczne dodanie nie można skompilować dla plików, na przykład *.xml*, *.txt*, lub pliki zasobów, do projektu programu SharePoint. Te pliki nie są automatycznie dostarczane w rozwiązaniu. Aby upewnić się, czy są pakowane, albo Dodaj pliki do zamapowany folder lub elementu projektu programu SharePoint.  
  
 Pliki dodane do folderów mapowanych są automatycznie kopiowane do gałęzi programu SharePoint, gdy rozwiązanie jest wdrożone. Pliki dodane do elementu projektu programu SharePoint są wdrażane do lokalizacji, która została określona w **lokalizacji wdrożenia** na podstawie właściwości dla każdego pliku, który częściowo ustawiono **typu wdrożenia** właściwości. Domyślnie **typu wdrożenia** wartość właściwości jest **NoDeployment**, co oznacza, że plik nie jest wdrażany za pomocą rozwiązania. Należy ustawić inną wartość dla właściwości dołączenie pliku do pakietu.  
  
 Na przykład, aby dodać *.xml* plik do projektu programu SharePoint, wykonaj jedną z następujących czynności:  
  
- Dodaj Folder mapowane "Układy" programu SharePoint do projektu. Spowoduje to utworzenie w **Eksploratora rozwiązań** folder o nazwie **układy** ma osobny podfolder dla projektu. Dodaj *.xml* plik do nowego podfolderu. Domyślnie plik jest wdrożony w systemie plików programu SharePoint w obszarze *... \TEMPLATE\LAYOUTS\\\<nazwę folderu >*. Aby uzyskać informacje dotyczące sposobu dodawania folderów mapowanych, zobacz [porady: Dodawanie i usuwanie folderów mapowanych](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
- Dodaj *.xml* pliku do folderu elementu projektu programu SharePoint, a następnie zmień **typu wdrożenia** właściwość *.xml* plik wchodzącej w skład **NoDeployment**  z innym ustawieniem dla takich jak **RootFile** lub **plik elementu**. Odpowiednie **typu wdrożenia** ustawienie zależy od projektu i pliku. Aby uzyskać więcej informacji na temat **typu wdrożenia** ustawienia właściwości, zobacz [rozwiązań SharePoint opracowywanie](../sharepoint/developing-sharepoint-solutions.md).  
  
  Jeżeli dodany plik nie ma zastosowania do żadnego konkretnego projektu w rozwiązaniu, można dodać pusty projekt programu SharePoint do rozwiązania i następnie dodać dodatkowe pliki do niego. Innym sposobem wdrażania plików dla programu SharePoint, szczególnie do bazy danych zawartości jest dodanie modułu do projektu, a następnie dodaj pliki do modułu. Aby uzyskać więcej informacji, zobacz [używać modułów podczas dołączania plików rozwiązania](../sharepoint/using-modules-to-include-files-in-the-solution.md).  
  
## <a name="see-also"></a>Zobacz także
 [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Kompilowanie i debugowanie rozwiązań SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
