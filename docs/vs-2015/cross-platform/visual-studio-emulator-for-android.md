---
title: Emulator programu Visual Studio dla systemu Android | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
ms.assetid: 80f0104f-a4db-44dd-bd55-37bb67776c62
caps.latest.revision: 7
ms.author: crdun
manager: crdun
ms.openlocfilehash: af3dd595b786c57983e44982fa2eb8b9afa2959a
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300768"
---
# <a name="visual-studio-emulator-for-android"></a>Emulator programu Visual Studio dla systemu Android
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio Emulator for Android to aplikacja klasyczna, która emuluje urządzenie z systemem Android. Zapewnia środowisko zwirtualizowane, w którym można debugować i testować aplikacje dla systemu Android bez urządzenia fizycznego. Zapewnia również środowisko izolowane dla prototypów aplikacji.  
  
 Emulator programu Visual Studio dla systemu Android został zaprojektowany w celu zapewnienia porównywalnej wydajności do rzeczywistego urządzenia. Jednak przed opublikowaniem aplikacji zalecamy przetestowanie aplikacji na urządzeniu fizycznym.  
  
 Możesz przetestować aplikację w unikatowym profilu urządzenia dla każdej platformy systemu Android, rozdzielczości ekranu i innych właściwości sprzętu obsługiwanych przez emulator programu Visual Studio dla systemu Android.  
  
 Ten temat zawiera następujące sekcje.  
  
- [Instalowanie i odinstalowywanie](#Installing)  
  
- [Wymagania systemowe i zgodność z poprzednimi wersjami](#Requirements)  
  
- [Obsługa sieci w emulatorze programu Visual Studio dla systemu Android](#Networking)  
  
- [Konfigurowanie emulatora programu Visual Studio dla systemu Android](#Configuring)  
  
- [Funkcje, które można testować w emulatorze](#FeaturesTest)  
  
- [Funkcje, których nie można testować w emulatorze](#FeaturesNonTest)  
  
- [Zasoby pomocy technicznej](#Support)  
  
## <a name="Installing"></a>Instalowanie i odinstalowywanie  
 Instalowanie programu  
  
 Program Visual Studio Emulator for Android to składnik wieloplatformowych narzędzi dostępnych w programie Visual Studio i zostanie zainstalowany podczas niestandardowej instalacji programu Visual Studio w przypadku wybrania wieloplatformowego opracowywania aplikacji mobilnych, a następnie wspólnych narzędzi i zestawów SDK. a następnie Emulator programu Visual Studio dla systemu Android.  
  
 Powiązane  
  
 Możesz odinstalować Emulator programu Visual Studio dla systemu Android za pomocą apletu Dodaj/Usuń programy w panelu sterowania.  
  
> [!NOTE]
> Odinstalowanie programu Visual Studio nie spowoduje odinstalowania emulatora. Należy odinstalować emulator osobno.  
  
 Po odinstalowaniu emulatora programu Visual Studio dla systemu Android, wirtualne karty sieciowe sieci Ethernet funkcji Hyper-V, które zostały utworzone dla emulatora, nie zostaną automatycznie usunięte. Możesz ręcznie usunąć te karty wirtualne (jeśli nie są używane), otwierając Menedżera funkcji Hyper-V, wybierając jeden z obrazów emulatora wirtualnego dysku twardego, wybierając kartę Sieć i wybierając pozycję **Usuń** dla każdego z przełączników, które pojawiają się na tej karcie.  
  
## <a name="Requirements"></a>Wymagania systemowe i zgodność z poprzednimi wersjami  
 Ważne informacje o wymaganiach dotyczących sprzętu, oprogramowania i konfiguracji dla programu Visual Studio Emulator for Android można znaleźć w następującym temacie.  
  
- [Wymagania systemowe dotyczące emulatora programu Visual Studio dla systemu Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)  
  
  Emulator programu Visual Studio dla systemu Android wymaga programu Visual Studio 2015; nie jest on zgodny z poprzednimi wersjami programu Visual Studio.  
  
  Nowe wersje emulatora są instalowane na podstawie starych wersji (i mogą w niektórych przypadkach zastąpić Stare obrazy, odrzucając ustawienia, aplikacje i pliki zainstalowane na tych obrazach).  
  
## <a name="Networking"></a>Obsługa sieci w emulatorze programu Visual Studio dla systemu Android  
 Połączenie sieciowe emulatora programu Visual Studio dla systemu Android zachowuje się jak połączenie komputera stacjonarnego o następujących cechach:  
  
- Emulator jest wyświetlany w sieci jako oddzielne urządzenie z własnym adresem IP.  
  
- Nie wymaga żadnych dodatkowych programów sieciowych, które nie są jeszcze zainstalowane z emulatorem.  
  
- Nie jest on przyłączony do domeny systemu Windows.  
  
  Aby poznać możliwości połączenia sieciowego emulatora, należy wziąć pod uwagę, że jest to podobne do połączenia Wi-Fi z telefonu z systemem Android z tą samą siecią. Jeśli aplikacja uruchomiona na telefonie ma dostęp do zasobu sieciowego za pośrednictwem połączenia Wi-Fi, wówczas aplikacja działająca na emulatorze może również uzyskać dostęp do tego samego zasobu sieciowego.  
  
  Aby uzyskać więcej informacji na temat wymagań sieci, zobacz [wymagania systemowe dla emulatora programu Visual Studio dla systemu Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)  
  
  Informacje o rozwiązywaniu problemów z siecią znajdują się w temacie [Rozwiązywanie problemów z programem Visual Studio Emulator for Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md).  
  
## <a name="Configuring"></a>Konfigurowanie emulatora programu Visual Studio dla systemu Android  
 Testowanie aplikacji systemu Android pod kątem zgodności między różnymi urządzeniami z systemem Android może być wyzwaniem. Telefony i tablety z systemem Android na rynku obejmują szeroką gamę wersji i rozmiary ekranu i są dostępne w wielu różnych konfiguracjach sprzętu (pamięć RAM, procesory CPU, architektura itp.). Emulator programu Visual Studio dla systemu Android upraszcza to przy użyciu profilów urządzeń. Nasz zbiór profilów urządzeń reprezentuje najpopularniejszy sprzęt na rynku, w tym urządzenia firmy Samsung, Motorola, Sony, LG i innych.  
  
 W programie Visual Studio 2015 można instalować, odinstalowywać i uruchamiać Profile urządzeń za pomocą Menedżera emulatorów. Uzyskaj dostęp do Menedżera emulatorów, wybierając **Narzędzia**, a następnie pozycję **Visual Studio Emulator for Android**.  
  
 ![Emulator programu Visual Studio dla systemu Android Manager](../cross-platform/media/android-emu-manager.png "Android_Emu_Manager")  
  
 Domyślnie są dostępne cztery wstępnie zainstalowane Profile urządzeń (konfiguracje KitKat i lizak telefonu/5 "i tablet/7"), jak wskazano biały tekst i ikony. Inne profile na liście pojawią się wyszarzone do momentu wybrania przycisku **Zainstaluj profil** i zakończenia instalacji. Możesz filtrować listę według poziomu interfejsu API i klikać strzałkę szczegółów w prawym dolnym rogu profilu, aby wyświetlić jego pełne szczegóły konfiguracji.  
  
 Po zainstalowaniu zestawu profili, które mają być przeznaczone do celów, możesz uruchomić te nowe profile bezpośrednio z poziomu Menedżera, naciskając zielony przycisk **Odtwórz** . Pojawią się one również w menu rozwijanym element docelowy debugowania w dowolnym typie projektu międzyplatformowego dla programu Visual Studio.  
  
## <a name="FeaturesTest"></a>Funkcje, które można testować w emulatorze  
 Aby uzyskać szczegółowe informacje na temat funkcji, które można testować w emulatorze, zapoznaj się z tą [dokumentacją](https://devblogs.microsoft.com/devops/introducing-visual-studios-emulator-for-android/).  
  
## <a name="FeaturesNonTest"></a>Funkcje, których nie można testować w emulatorze  
 Poniższa lista zawiera opis funkcji platformy systemu Android, których **nie można** przetestować w emulatorze. Należy przetestować te funkcje na urządzeniu fizycznym.  
  
- Kompas  
  
- Żyroskop  
  
- Kontroler drgań  
  
- Jasność. Zmiana poziomu jasności emulatora nie wpłynie wizualnie na wygląd urządzenia na ekranie.  
  
## <a name="Support"></a> Zasoby pomocy technicznej  
 Jeśli komputer-host spełnia wymagania systemowe i wystąpi problem, nie są uwzględnione w tym przewodniku rozwiązywania problemów:  
  
- Zadawaj pytanie dotyczące StackOverflow przy użyciu [emulatora systemu Android](https://stackoverflow.com/questions/tagged/android-emulator) i programu Visual Studio.  
  
- Zgłoś problem za pomocą Wyślij uśmiech narzędzia programu Visual Studio lub w Menedżerze emulatorów.  
  
## <a name="see-also"></a>Zobacz też  
 [Wymagania systemowe dotyczące programu Visual Studio Emulator dla systemu Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)   
 [Rozwiązywanie problemów z emulatorem programu Visual Studio dla systemu Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)
