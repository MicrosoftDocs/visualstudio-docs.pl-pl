---
title: Usługi połączone
description: Dodaj magazyn danych na platformie Azure, uwierzytelnianie i powiadomienia wypychane do aplikacji mobilnych z poziomu programu Visual Studio dla komputerów Mac
ms.assetid: 41CB62FF-0F39-4CE8-8917-6A77F058719F
author: sayedihashimi
ms.author: sayedha
ms.date: 11/06/2018
ms.openlocfilehash: 34a4344be0e48d41829a7bf7df660a91d4f897b6
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67693089"
---
# <a name="connected-services-walkthrough"></a>Połączone usługi wskazówki

Podłączone usługi przepływu pracy umożliwia Azure portal przepływu pracy w programie Visual Studio, dla komputerów Mac, dzięki czemu nie trzeba pozostaw projekt, aby dodać usługi.

W tym instruktażu przedstawiono sposób dodawania usługi zaplecza platformy Azure, który udostępnia magazyn danych w chmurze, uwierzytelnianie i powiadomienia wypychane do aplikacji platformy Xamarin.Forms biblioteki klas przenośnych (PCL) dla wielu platform.

1. Uruchomić przez dwukrotne kliknięcie **podłączone usługi** węzła w rozwiązaniu, co umożliwia wyświetlenie **galerii usługi**.
  To jest lista usług dostępnych dla typu aplikacji. Wybierz usługę (takie jak **zaplecza aplikacji mobilnych w usłudze Azure App Service**), klikając ją.

    [![Połączone węzła usług w programie Visual Studio dla komputerów Mac](media/connected-services-image001-sml.png "węzła usług połączonych programu Visual Studio dla komputerów Mac")](media/connected-services-image001.png#lightbox)

2. Strona Szczegóły usługi zawiera opis usługi i zależności do zainstalowania.
  Kliknij przycisk **Dodaj** przycisk, aby dodać zależności do aplikacji:

    [![Zaplecza aplikacji mobilnych za pomocą platformy Azure](media/connected-services-image002-sml.png "zaplecza aplikacji mobilnych za pomocą platformy Azure")](media/connected-services-image002.png#lightbox)

3. Zależności muszą zostać dodane do PCL i projektów specyficznych dla platformy do pracy.
  Zaznacz pola wyboru, aby dodać usługę do każdego projektu, który zostanie do niego odwołują (bezpośrednio lub pośrednio):

    [![Sprawdź wszystkie projekty, które powinny odwoływać się do usługi](media/connected-services-image003-sml.png "Sprawdź wszystkie projekty, które powinny odwoływać się do usługi")](media/connected-services-image003.png#lightbox)

4. Wybierz **Akceptuj** na **akceptacja licencji** dialogów dla pakietów NuGet.
  Może to być dwa okien dialogowych, aby zaakceptować, jeden dla MobileClient i zależności i inny wpis dla SQLiteStore, co jest wymagane w celu synchronizacji danych w trybie offline:

    [![Zaakceptuj umowy licencyjne](media/connected-services-image004-sml.png "Zaakceptuj umowy licencyjne")](media/connected-services-image004.png#lightbox)

    ![Okno akceptacja licencji](media/connected-services-image005.png "okna akceptacji licencji")

5. Po dodaniu zależności, użytkownik zostanie zapytany logowanie się przy użyciu konta którego chcesz używać do komunikowania się z platformą Azure.
  Jeśli masz już zalogowano się za pomocą Identyfikatora firmy Microsoft, Visual Studio for Mac będzie podejmować próby pobrania subskrypcji platformy Azure i usług aplikacji skojarzonych z nimi. Jeśli nie masz żadnych subskrypcji, możesz dodać za rejestrację w usłudze bezpłatnej wersji próbnej lub zakup planu subskrypcji w witrynie Azure portal.

6. Wybierz usługę app service z listy. Spowoduje to wypełnienie kod szablonu dla `MobileServiceClient` obiektu przy użyciu odpowiedniego adresu URL usługi app Service na platformie Azure:

    [![Wybierz usługi app service z listy](media/connected-services-image006-sml.png "z listy wybierz usługi app service")](media/connected-services-image006.png#lightbox)

    W przypadku ma usług na liście, kliknij przycisk **New** przycisku (zobacz krok 9).

7. Skopiuj kod szablonu `MobileServiceClient` do PCL. Lokalizacja pliku nie jest istotne, tak długo, jak istnieje tylko jedno wystąpienie.
  Zalecaną metodą jest utworzenie `AzureService` klasę, która obsługuje wszystkie interakcje platformy Azure i korzysta z `MobileServiceClient`:

    ![Skopiuj kod konfiguracji do ap](media/connected-services-image007.png "skopiować kod konfiguracji do aplikacji")

8. Postępuj zgodnie z dokumentacją w **następne kroki** do dodawania danych, synchronizacji w trybie offline, uwierzytelnianie i powiadomienia wypychane do aplikacji:

    [![Przejrzyj następnej instrukcji kroki](media/connected-services-image008-sml.png "przejrzeć instrukcje dla następnej czynności")](media/connected-services-image008.png#lightbox)

9. Jeśli nie masz żadnych istniejących usług aplikacji, można utworzyć nowych usług z poziomu programu Visual Studio dla komputerów Mac.
  Kliknij przycisk **New** przycisku w lewym dolnym rogu listy usług w celu otwarcia **nowej usługi App Service** okno dialogowe:

    [![Utwórz nową usługę app service w programie Visual Studio dla komputerów Mac](media/connected-services-image009-sml.png "Tworzenie nowej usługi app service w programie Visual Studio dla komputerów Mac")](media/connected-services-image009.png#lightbox)

Nowa usługa wymaga następujących parametrów:

- **Nazwa usługi App service** — unikatowe nazwy/identyfikatora dla tego planu
- **Subskrypcja** — subskrypcji, o których chcesz użyć do zapłacenia za usługę
- **Grupa zasobów** — lub sposób organizowania wszystkich zasobów platformy Azure dla projektu. Opcja Użyj istniejącej lub utworzyć nowy. Jeśli jest to pierwszy usługi platformy Azure, Utwórz nową.
- **Plan usługi** — Określa lokalizację i koszt zasobów, które go używają. Opcja Użyj istniejącej lub utworzyć nowy. Jeśli jest to pierwszy usługi platformy Azure, użyj wartości domyślnej, jeden lub Utwórz nową (F1) w warstwie bezpłatna.

Odwiedź stronę [dokumentacja usługi Mobile apps](/azure/app-service-mobile/) Aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz także

- [Połączone usługi (Visual Studio Windows)](/visualstudio/azure/vs-azure-tools-connected-services-storage)