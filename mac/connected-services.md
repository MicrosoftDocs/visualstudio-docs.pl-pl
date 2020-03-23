---
title: Usługi połączone
description: Dodawanie do aplikacji mobilnych magazynu danych, uwierzytelniania i powiadomień wypychanych platformy Azure z poziomu programu Visual Studio dla komputerów Mac
ms.assetid: 41CB62FF-0F39-4CE8-8917-6A77F058719F
author: sayedihashimi
ms.author: sayedha
ms.date: 11/06/2018
ms.openlocfilehash: 34a4344be0e48d41829a7bf7df660a91d4f897b6
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "67693089"
---
# <a name="connected-services-walkthrough"></a>Przewodnik po połączonych usługach

Przepływ pracy usług połączonych przenosi przepływ pracy portalu Azure do programu Visual Studio dla komputerów Mac, więc nie trzeba opuszczać projektu, aby dodać usługi.

W tym przewodniku pokazano, jak dodać usługę wewnętrznej bazy danych platformy Azure, która przynosi przechowywanie danych w chmurze, uwierzytelnianie i powiadomienia wypychania do wieloplatformowej aplikacji Xamarin.Forms Portable Class Library (PCL).

1. Zacznij od dwukrotnego kliknięcia węzła **Usługi połączone** w rozwiązaniu, który powoduje wyświetlenie **Galerii usług**.
  Jest to lista wszystkich dostępnych usług dla typu aplikacji. Wybierz usługę (na przykład **zaplecze mobilne z usługą Azure App Service),** klikając ją.

    [![Węzeł Połączone usługi w programie Visual Studio dla komputerów Mac](media/connected-services-image001-sml.png "Węzeł Połączone usługi w programie Visual Studio dla komputerów Mac")](media/connected-services-image001.png#lightbox)

2. Strona Szczegóły usługi zawiera opis usługi i zależności, które mają zostać zainstalowane.
  Kliknij przycisk **Dodaj,** aby dodać zależności do aplikacji:

    [![Zaplecze mobilne za pomocą platformy Azure](media/connected-services-image002-sml.png "Zaplecze mobilne za pomocą platformy Azure")](media/connected-services-image002.png#lightbox)

3. Zależności muszą zostać dodane do projektów PCL i specyficznych dla platformy do pracy.
  Zaznacz pola wyboru, aby dodać usługę do każdego projektu, który będzie się do niej odwoływał (bezpośrednio lub pośrednio):

    [![Sprawdź wszystkie projekty, które powinny odwoływać się do usługi](media/connected-services-image003-sml.png "Sprawdź wszystkie projekty, które powinny odwoływać się do usługi")](media/connected-services-image003.png#lightbox)

4. Wybierz **pozycję Zaakceptuj** w oknach dialogowych **akceptacji licencji** dla pakietów NuGet.
  Mogą istnieć dwa okna dialogowe do zaakceptowania, jeden dla MobileClient i zależności, a drugi dla SQLiteStore, który jest wymagany do synchronizacji danych w trybie offline:

    [![Akceptuj umowy licencyjne](media/connected-services-image004-sml.png "Akceptuj umowy licencyjne")](media/connected-services-image004.png#lightbox)

    ![Okno Akceptacja licencji](media/connected-services-image005.png "Okno Akceptacja licencji")

5. Po dodaniu zależności zostaniesz poproszony o zalogowanie się przy użyciu konta, którego chcesz użyć do komunikowania się z platformą Azure.
  Jeśli jesteś już zalogowany przy pomocy identyfikatora Microsoft ID, program Visual Studio dla komputerów Mac podejmie próbę pobrania subskrypcji platformy Azure i wszystkich usług aplikacji skojarzonych z nimi. Jeśli nie masz żadnych subskrypcji, możesz dodać jedną, rejestrując się w celu bezpłatnej wersji próbnej lub kupując plan subskrypcji w witrynie Azure portal.

6. Wybierz usługę aplikacji z listy. Spowoduje to wypełnienie kodu `MobileServiceClient` szablonu obiektu odpowiednim adresem URL usługi aplikacji na platformie Azure:

    [![Wybieranie usługi aplikacji z listy](media/connected-services-image006-sml.png "Wybieranie usługi aplikacji z listy")](media/connected-services-image006.png#lightbox)

    Jeśli na liście nie ma żadnych usług, kliknij przycisk **Nowy** (zobacz krok 9).

7. Skopiuj `MobileServiceClient` kod szablonu do PCL. Lokalizacja pliku nie jest ważna, o ile istnieje tylko jedno wystąpienie.
  Zalecane podejście polega na `AzureService` utworzeniu klasy obsługującej wszystkie `MobileServiceClient`interakcje platformy Azure i korzystającej z:

    ![Kopiowanie kodu konfiguracyjnego do ap](media/connected-services-image007.png "Kopiowanie kodu konfiguracji do aplikacji")

8. Postępuj zgodnie z dokumentacją w **następnych krokach,** aby dodać do aplikacji dane, synchronizację w trybie offline, uwierzytelnianie i powiadomienia wypychane:

    [![Zapoznaj się z instrukcjami dotyczącymi kolejnych kroków](media/connected-services-image008-sml.png "Zapoznaj się z instrukcjami dotyczącymi kolejnych kroków")](media/connected-services-image008.png#lightbox)

9. Jeśli nie masz żadnych istniejących usług aplikacji, możesz utworzyć nowe usługi z poziomu programu Visual Studio dla komputerów Mac.
  Kliknij przycisk **Nowy** w lewym dolnym rogu listy usług, aby otworzyć okno dialogowe **Nowa usługa aplikacji:**

    [![Tworzenie nowej usługi aplikacji w programie Visual Studio dla komputerów Mac](media/connected-services-image009-sml.png "Tworzenie nowej usługi aplikacji w programie Visual Studio dla komputerów Mac")](media/connected-services-image009.png#lightbox)

Nowa usługa wymaga następujących parametrów:

- **Nazwa usługi aplikacji** — unikatowa nazwa/identyfikator planu
- **Subskrypcja** – subskrypcja, której chcesz użyć, aby zapłacić za usługę
- **Grupa zasobów** — sposób lub organizowanie wszystkich zasobów platformy Azure dla projektu. Opcja użycia istniejącego lub utworzenia nowego. Jeśli jest to twoja pierwsza usługa platformy Azure, utwórz nową.
- **Plan usług** — określa lokalizację i koszt wszystkich zasobów, które go używają. Opcja użycia istniejącego lub utworzenia nowego. Jeśli jest to twoja pierwsza usługa platformy Azure, użyj domyślnej lub utwórz nową w warstwie bezpłatnej (F1).

Więcej informacji można znaleźć w [dokumentacji aplikacji mobilnych.](/azure/app-service-mobile/)

## <a name="see-also"></a>Zobacz też

- [Połączone usługi (Visual Studio w systemie Windows)](/visualstudio/azure/vs-azure-tools-connected-services-storage)