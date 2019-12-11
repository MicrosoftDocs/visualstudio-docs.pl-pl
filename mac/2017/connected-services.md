---
title: Usługi połączone
description: Dodawanie usługi Azure Data Storage, uwierzytelniania i powiadomień wypychanych do aplikacji mobilnych z poziomu Visual Studio dla komputerów Mac
ms.assetid: 41CB62FF-0F39-4CE8-8917-6A77F058719F
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/06/2018
ms.openlocfilehash: 241820de009a5118869583bbe228ecb0604f9001
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74985290"
---
# <a name="connected-services-walkthrough"></a>Przewodnik po usługach połączonych

Przepływ pracy podłączonych usług przenosi przepływ pracy Azure Portal do Visual Studio dla komputerów Mac, dzięki czemu nie trzeba opuszczać projektu do dodawania usług.

W tym instruktażu pokazano, jak dodać usługę zaplecza platformy Azure, która umożliwia przechowywanie danych w chmurze, uwierzytelnianie i powiadomienia wypychane do wieloplatformowej aplikacji Xamarin. Forms w technologii Portable Class Library (PCL).

1. Zacznij od dwukrotnego kliknięcia węzła **usługi połączone** w rozwiązaniu, co spowoduje wyświetlenie **galerii usług**.
  Jest to lista wszystkich dostępnych usług dla typu aplikacji. Wybierz usługę (na przykład **zaplecze Mobile with Azure App Service**), klikając ją.

    [![Węzeł usługi połączone w Visual Studio dla komputerów Mac](media/connected-services-image001-sml.png "Węzeł usługi połączone w Visual Studio dla komputerów Mac")](media/connected-services-image001.png#lightbox)

2. Na stronie Szczegóły usługi znajduje się opis usługi i zależności, które mają zostać zainstalowane.
  Kliknij przycisk **Dodaj** , aby dodać zależności do aplikacji:

    [![Zaplecze mobilne z platformą Azure](media/connected-services-image002-sml.png "Zaplecze mobilne z platformą Azure")](media/connected-services-image002.png#lightbox)

3. Aby działały, należy dodać zależności do projektów PCL i dla konkretnych platform.
  Zaznacz pola wyboru, aby dodać usługę do każdego projektu, który będzie odwoływać się do niego (bezpośrednio lub pośrednio):

    [![Sprawdź wszystkie projekty, które powinny odwoływać się do usługi](media/connected-services-image003-sml.png "Sprawdź wszystkie projekty, które powinny odwoływać się do usługi")](media/connected-services-image003.png#lightbox)

4. Wybierz pozycję **Zaakceptuj** w oknach dialogowych **akceptacji licencji** dla pakietów NuGet.
  Mogą istnieć dwa okna dialogowe do zaakceptowania, jeden dla MobileClient i zależności oraz drugi dla SQLiteStore, który jest wymagany do synchronizacji danych w trybie offline:

    [![Akceptuj umowy licencyjne](media/connected-services-image004-sml.png "Akceptuj umowy licencyjne")](media/connected-services-image004.png#lightbox)

    ![Okno akceptacji licencji](media/connected-services-image005.png "Okno akceptacji licencji")

5. Po dodaniu zależności zostanie wyświetlony monit o zalogowanie się przy użyciu konta, którego chcesz używać do komunikowania się z platformą Azure.
  Jeśli użytkownik jest już zalogowany przy użyciu identyfikatora firmy Microsoft, Visual Studio dla komputerów Mac podejmie próbę pobrania subskrypcji platformy Azure i skojarzonych z nimi usług App Services. Jeśli nie masz żadnych subskrypcji, możesz je dodać, rejestrując się w celu skorzystania z bezpłatnej wersji próbnej lub zakupienia planu subskrypcji w Azure Portal.

6. Wybierz z listy usługę App Service. Spowoduje to wypełnienie kodu szablonu dla obiektu `MobileServiceClient` przy użyciu odpowiedniego adresu URL usługi App Service na platformie Azure:

    [![Wybierz usługę App Service z listy](media/connected-services-image006-sml.png "Wybierz usługę App Service z listy")](media/connected-services-image006.png#lightbox)

    Jeśli na liście nie ma żadnych usług, kliknij przycisk **Nowy** (zobacz krok 9).

7. Skopiuj kod szablonu dla `MobileServiceClient` do PCL. Lokalizacja pliku nie jest ważna, pod warunkiem, że istnieje tylko jedno wystąpienie.
  Zalecanym podejściem jest utworzenie klasy `AzureService`, która obsługuje wszystkie interakcje platformy Azure i używa `MobileServiceClient`:

    ![Kopiuj kod konfiguracyjny do AP](media/connected-services-image007.png "Kopiuj kod konfiguracji do aplikacji")

8. Postępuj zgodnie z dokumentacją w **sekcji Następne kroki** , aby dodać dane, synchronizację w trybie offline, uwierzytelnianie i powiadomienia wypychane do aplikacji:

    [![Zapoznaj się z instrukcjami dotyczącymi następnych kroków](media/connected-services-image008-sml.png "Zapoznaj się z instrukcjami dotyczącymi następnych kroków")](media/connected-services-image008.png#lightbox)

9. Jeśli nie masz żadnych istniejących usług App Services, możesz utworzyć nowe usługi z poziomu Visual Studio dla komputerów Mac.
  Kliknij przycisk **Nowy** w lewym dolnym rogu listy usługi, aby otworzyć okno dialogowe **nowe App Service** :

    [![Utwórz nową usługę App Service w Visual Studio dla komputerów Mac](media/connected-services-image009-sml.png "Utwórz nową usługę App Service w Visual Studio dla komputerów Mac")](media/connected-services-image009.png#lightbox)

Nowa usługa wymaga następujących parametrów:

- **Nazwa usługi App Service** — unikatowa nazwa/identyfikator planu
- **Subskrypcja** — subskrypcja, której chcesz użyć do płacenia za usługę
- **Grupa zasobów** — sposób lub organizacja wszystkich zasobów platformy Azure dla projektu. Opcja użycia istniejącej lub tworzenia nowej. Jeśli jest to Twoja pierwsza usługa platformy Azure, Utwórz nową.
- **Plan usługi** — określa lokalizację i koszt wszystkich zasobów, które z nich korzystają. Opcja użycia istniejącej lub tworzenia nowej. Jeśli jest to Twoja pierwsza usługa platformy Azure, Użyj domyślnej lub Utwórz nową w warstwie Bezpłatna (F1).

Aby uzyskać więcej informacji, odwiedź [dokumentację aplikacji mobilnych](/azure/app-service-mobile/) .

## <a name="see-also"></a>Zobacz także

- [Usługi połączone (Visual Studio w systemie Windows)](/visualstudio/azure/vs-azure-tools-connected-services-storage)