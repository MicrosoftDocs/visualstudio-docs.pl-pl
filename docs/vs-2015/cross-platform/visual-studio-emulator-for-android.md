---
title: Visual Studio Emulator for Android | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
ms.assetid: 80f0104f-a4db-44dd-bd55-37bb67776c62
caps.latest.revision: 7
ms.author: crdun
manager: crdun
ms.openlocfilehash: a33d7928e6e2555f0cfd484059b062ae801d8633
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442085"
---
# <a name="visual-studio-emulator-for-android"></a>Emulator programu Visual Studio dla systemu Android
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio Emulator for Android to aplikacja komputerowa, która emuluje urządzenie z systemem Android. Umożliwia środowisku wirtualnym, w którym można debugowanie i testowanie aplikacji dla systemu Android bez fizycznego urządzenia. Umożliwia także izolowanym środowisku na potrzeby prototypów aplikacji.  
  
 Visual Studio Emulator for Android zaprojektowano w celu zapewnienia wydajności porównywalne do rzeczywistego urządzenia. Przed opublikowaniem aplikacji, jednak Zalecamy przetestowanie aplikacji na urządzeniu fizycznym.  
  
 Możesz przetestować swoją aplikację w profilu urządzenia unikatowy dla każdej platformy systemu Android, rozdzielczość ekranu i innych właściwości sprzętu, obsługiwane przez Visual Studio Emulator for Android.  
  
 Ten temat zawiera następujące sekcje.  
  
- [Instalowanie i odinstalowywanie](#Installing)  
  
- [Wymagania systemowe i zgodność z poprzednimi wersjami](#Requirements)  
  
- [Sieci w programie Visual Studio Emulator for Android](#Networking)  
  
- [Konfigurowanie programu Visual Studio Emulator for Android](#Configuring)  
  
- [Funkcje, które można przetestować w emulatorze](#FeaturesTest)  
  
- [Funkcje, które nie możesz przetestować w emulatorze](#FeaturesNonTest)  
  
- [Zasoby pomocy technicznej](#Support)  
  
## <a name="Installing"></a> Instalowanie i odinstalowywanie  
 Instalowanie programu  
  
 Visual Studio Emulator for Android jest składnikiem narzędzi dla wielu platform, dostępnych w programie Visual Studio i zostanie zainstalowany podczas instalacji niestandardowej programu Visual Studio, po wybraniu Cross-Platform Mobile Development, a następnie typowe narzędzia i zestawy Software Development Kit a następnie w programie Visual Studio Emulator for Android.  
  
 Odinstalowywanie  
  
 Można odinstalować Visual Studio Emulator dla systemu Android za pomocą opcji Dodaj/Usuń programy w Panelu sterowania.  
  
> [!NOTE]
> Odinstalowywanie programu Visual Studio nie spowoduje odinstalowania emulatora. Należy odinstalować emulator oddzielnie.  
  
 Po odinstalowaniu programu Visual Studio Emulator for Android funkcji Hyper-V wirtualne karty Ethernet utworzone dla emulatora do użycia nie są automatycznie usuwane. Można ręcznie usunąć tych wirtualnych kart sieciowych (jeśli jest nieużywany), otwierając Menedżera funkcji Hyper-V, wybierając jedną z emulator obrazów wirtualnych dysków Twardych, wybierając kartę Sieć i wybierając **Usuń** dla wszystkich przełączników, które pojawia się na tej karcie.  
  
## <a name="Requirements"></a> Wymagania systemowe i zgodność z poprzednimi wersjami  
 Aby uzyskać ważne informacje na temat sprzętu, oprogramowania i wymagań dotyczących konfiguracji programu Visual Studio Emulator for Android zobacz następujący temat.  
  
- [Wymagania systemowe dotyczące emulatora programu Visual Studio dla systemu Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)  
  
  Visual Studio Emulator for Android wymaga programu Visual Studio 2015; nie jest zgodne z poprzednimi wersjami z wcześniejszymi wersjami programu Visual Studio.  
  
  Nowe wersje emulatora są instalowane na starsze wersje (i w niektórych przypadkach może zastąpić starych obrazów, odrzucając ustawień aplikacji i plików instalowanych w tych obrazów).  
  
## <a name="Networking"></a> Sieci w programie Visual Studio Emulator for Android  
 Sieciowe połączenie programu Visual Studio Emulator dla systemu Android zachowuje się jak połączenie komputera stacjonarnego z następującą charakterystyką:  
  
- Emulator jest traktowany jako oddzielne urządzenia przy użyciu adresu IP w sieci.  
  
- Nie jest wymagane dodatkowe oprogramowanie sieciowe, który nie został jeszcze zainstalowany za pomocą emulatora.  
  
- Nie jest przyłączony do domeny Windows.  
  
  Aby poznać możliwości połączenia sieciowego to emulator, go traktować jako podobny do połączenia sieci Wi-Fi na telefonie z systemem Android z tą samą siecią. Jeśli działanie aplikacji na telefonie dostęp do zasobów sieciowych za pośrednictwem połączenia sieci Wi-Fi, w aplikacji uruchomionej w emulatorze można także używać tego samego zasobu sieciowego.  
  
  Aby uzyskać więcej informacji na temat wymagań sieciowych, zobacz [wymagania systemowe programu Visual Studio Emulator for Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)  
  
  Aby uzyskać informacje na temat rozwiązywania problemów w sieci, zobacz [Rozwiązywanie problemów z emulatorem programu Visual Studio dla systemu Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md).  
  
## <a name="Configuring"></a> Konfigurowanie programu Visual Studio Emulator for Android  
 Testowanie aplikacji systemu Android w celu zachowania zgodności różnych różnicowanie sprzętu może być trudne. Telefony z systemem android tabletów na rynku obejmują szeroki zakres wersji i rozmiarów ekranu i są dostępne w wielu różnych konfiguracji sprzętu (ilość pamięci RAM, procesory, architektura itp.). Visual Studio Emulator for Android upraszcza to przy użyciu profilów urządzeń. Nasz zestaw profilów urządzeń reprezentuje najpopularniejszy sprzęt na rynku, w tym urządzenia firmy Samsung, Motorola, Sony, LG i innych.  
  
 W programie Visual Studio 2015 można zainstalować, odinstalować i uruchomić profile urządzeń przy użyciu Menedżera emulatora. Dostęp do Menedżera emulatora, wybierając **narzędzia**, następnie **Visual Studio Emulator for Android**.  
  
 ![Emulator programu Visual Studio dla systemu Android Menedżera](../cross-platform/media/android-emu-manager.png "Android_Emu_Manager")  
  
 Domyślnie istnieją cztery profile wstępnie zainstalowane urządzenie (KitKat i Lollipop telefonu na dobę, 5 "i tabletów 7 dni w tygodniu" konfiguracji), wskazane przez białego tekstu i ikony. Inne profile na liście będą wyszarzone dopóki nie wybierzesz **Instalowanie profilu** przycisku i instalacji ukończenia. Można filtrować listę według poziom interfejsu API i kliknij strzałkę szczegółów na dole po prawej stronie profilu, aby wyświetlić jego szczegóły pełną konfigurację.  
  
 Po zainstalowaniu zbiór profilów, które chcesz pod kątem tych nowych profili można uruchomić bezpośrednio z Menedżera, naciskając klawisz na zielony wskaźnik **Odtwórz** przycisku. Również pojawią się one w menu rozwijanym docelowy debugowania w dowolnym typem projektu mobilnych między platformami Visual Studio.  
  
## <a name="FeaturesTest"></a> Funkcje, które można przetestować w emulatorze  
 Aby uzyskać szczegółowe informacje na temat funkcji, możesz przetestować w emulatorze, zobacz ten [dokumentacji](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/12/introducing-visual-studio-s-emulator-for-android.aspx).  
  
## <a name="FeaturesNonTest"></a> Funkcje, które nie możesz przetestować w emulatorze  
 Na poniższej liście opisano funkcje platformy systemu Android, **nie** testu w emulatorze. Masz do badania tych funkcji na urządzeniu fizycznym.  
  
- Kompas  
  
- Żyroskop  
  
- Wibracje kontrolera  
  
- Jasność. Zmiana poziomu jasności emulatora nie wizualnie wpływają na sposób, w których urządzenie znajduje się na ekranie.  
  
## <a name="Support"></a> Zasoby pomocy technicznej  
 Jeśli komputer-host spełnia wymagania systemowe i wystąpi problem, nie są uwzględnione w tym przewodniku rozwiązywania problemów:  
  
- Zadaj pytanie na temat korzystania z StackOverflow [emulator systemu android](http://stackoverflow.com/questions/tagged/android-emulator) oraz tag visual studio.  
  
- Zgłoś problem za pomocą Wyślij uśmiech narzędzia programu Visual Studio lub w Menedżerze emulatorów.  
  
## <a name="see-also"></a>Zobacz też  
 [Wymagania systemowe dotyczące emulatora programu Visual Studio dla systemu Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)   
 [Rozwiązywanie problemów z emulatorem programu Visual Studio dla systemu Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)
