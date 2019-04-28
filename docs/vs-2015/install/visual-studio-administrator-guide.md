---
title: Podręcznik administratora programu Visual Studio | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
caps.latest.revision: 76
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 5a84f0a037df92ff31ce66eb6692367ef1d209f6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546664"
---
# <a name="visual-studio-administrator-guide"></a>Podręcznik administratora programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio, zobacz [Podręcznik administratora programu Visual Studio](/visualstudio/install/visual-studio-administrator-guide).

Visual Studio 2015 można wdrożyć w sieci, tak długo, jak długo każdy komputer docelowy spełnia [minimalne wymagania dotyczące instalacji](https://visualstudio.microsoft.com/vs/older-downloads/). Można utworzyć udział sieciowy, uruchamiając plik instalacyjny z przełącznikiem/Layout (zgodnie z opisem na [trybu Offline instalacji programu Visual Studio Utwórz](../install/create-an-offline-installation-of-visual-studio.md) strony), a następnie kopiując je z komputera lokalnego do udziału sieciowego. Jeśli używasz obrazu ISO, możesz zainstalować plik ISO i udostępnić go lub skopiuj plik ISO w udziale sieciowym.  
  
 Należy pamiętać, że instalacji z udziału sieciowego "Pamiętaj" lokalizacji źródłowej, które pochodzą z. Oznacza to, naprawy maszyny klienta może być konieczne powrócić do udziału sieciowego, który pierwotnie zainstalowany klient z. Wybierz lokalizację sieci dokładnie tak, aby powoduje wyrównanie z okresem istnienia spodziewasz się klientów programu Visual Studio 2015 w Twojej organizacji.  
  
## <a name="detection-and-servicing-keys"></a>Wykrywanie i Obsługa kluczy  
 Wykrywania podkluczy w rejestrze służy do określenia, czy produkt Visual Studio jest już zainstalowana na komputerze. Te klucze wykrywania w automatycznego wdrażania należy użyć do określenia, czy był to konieczne kontynuować instalację.  Zobacz [wykrywanie wymagań systemowych](../extensibility/internals/detecting-system-requirements.md)[wykrywanie wymagań systemowych].  
  
## <a name="avoiding-reboots"></a>Unikanie ponownego uruchamiania  
 Można zmniejszyć ponownych rozruchów, upewniając się, że spełniają odpowiednie wymagania wstępne dotyczące programu Visual Studio przed wdrożeniem programu Visual Studio. Dla programu .NET Framework może być konieczne ponowne uruchomienie komputerów z systemem Windows 8 w przypadku wdrożenia programu Visual Studio 2015 na nich bez instalowania najpierw oprogramowania .NET Framework 4.6.  
  
 Emulacji urządzenia Windows i Android może być konieczne ponowne uruchomienie komputerów, jeśli nie masz jeszcze funkcji Windows Hyper-V jest włączona. Do tworzenia aplikacji internetowych może być konieczne ponowne uruchomienie komputerów, jeśli nie masz jeszcze przez serwer sieci Web jest włączona funkcja Windows. Do tworzenia aplikacji pakietu Office może być konieczne ponowne uruchomienie komputerów, jeśli nie masz jeszcze funkcji Windows Foundation zidentyfikować Windows jest włączona. Jeśli nie masz jeszcze przez serwer sieci Web jest włączona funkcja Windows, należy ponownie uruchomić komputery. Do tworzenia aplikacji pakietu Office może być konieczne ponowne uruchomienie komputerów, jeśli nie masz jeszcze funkcji Windows Foundation zidentyfikować Windows jest włączona. Aby dowiedzieć się więcej o tym, jak zautomatyzować wykrywania i instalację funkcji Windows, zobacz [instalowania roli serwera na serwerze z uruchomioną instalacją Server Core systemu Windows Server 2008 R2](https://technet.microsoft.com/library/ee441260(v=ws.10).aspx).  
  
## <a name="error-return-codes"></a>Kody powrotne błędów  
 Poniższa tabela zawiera listę kodów ważnych błędów. Te kody błędów w automatyzacji służy do określenia, czy wymagany jest ponowny rozruch, i czy Instalacja powiodła się. Jeśli zostanie wyświetlony kod błędu, należy wziąć pod uwagę kroki rozwiązywania problemów na [Zainstaluj program Visual Studio](../install/install-visual-studio-2015.md) strony.  
  
|Stan instalacji|Ponowne uruchomienie nie jest wymagane|Ponowne uruchomienie jest wymagane|Opis|  
|------------------|--------------------------|----------------------|-----------------|  
|Powodzenie|0x00000000 [0]|0x00000bc2 [3010]|Instalacja zakończona pomyślnie.|  
|Blok|0x80044000 [-2147205120]|0x8004C000 [-2147172352]|Jeśli jedynym blokiem do zgłaszania jest "Oczekiwanie na ponowne uruchomienie", zwrócona wartość jest rozruchu niekompletnego ponownego (0x80048bc7).|  
|Anuluj|0x00000642 [1602]|0x80048642 [-2147187134]|Po ponownym uruchomieniu wartość jest zwracana, kod zwrotny jest 1602.|  
|Niekompletne — wymagany jest ponowny rozruch|Brak|0x80048bc7 [-2147185721]|Wymagane jest ponowne uruchomienie, zanim będzie można kontynuować instalacji.|  
|Błąd|0x00000643 [1603]|0x80048643 [-2147187133]|Po ponownym uruchomieniu wartość jest zwracana, kod zwrotny jest 1603.|  
  
## <a name="interactive-administrator-installer"></a>Instalator administratora interaktywnego  
 Jeśli tworzysz interakcyjnego Instalatora na instalację programu Visual Studio, możesz wyświetlić postęp w Instalatorze programu Visual Studio. Visual Studio 2015, które Instalator jest oparta na "Open source" technologii chainer XML Instalatora Windows (WiX), znany także jako "Nagraj." Technologia nagrywania obsługuje dwa protokoły komunikacyjne: nagrywania i netfx4. Krótki opis odwołania, zobacz opis atrybutu protokołu w dokumentacji dla elementu ExePackage na [wixtoolset.org](http://wixtoolset.org/). Przegląd wdrożenia "open source" WiX tego atrybutu protokołu mogą być wymagane dla integracji.  
  
## <a name="controlling-what-is-installed"></a>Kontrolowanie, co jest zainstalowany  
 Jeśli chcesz kontrolować, jakie można zainstalować użytkownikowi końcowemu, dostępne są dwie opcje: administrator plików instalacji i opcje wiersza polecenia. Wybierz instalację pliku administratora, jeśli dowiesz się, jak ograniczyć użytkownikowi końcowemu korzystać z ich działanie Instalatora programu Visual Studio. Wybierz parametry wiersza polecenia utworzyć początkową konfigurację, ale Zezwalaj użytkownikowi końcowemu wybrać własne środowisko Instalatora programu Visual Studio.  
  
 Aby uzyskać więcej informacji na temat doświadczeń pliku administratora, zobacz [jak: Utworzyć i uruchomić nienadzorowaną instalację programu Visual Studio](../install/how-to-create-and-run-an-unattended-installation-of-visual-studio.md) i [jak: Automatyczne stosowanie kluczy produktów podczas wdrażania programu Visual Studio](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md).  Aby uzyskać więcej informacji na temat opcji wiersza polecenia, zobacz [Użyj parametrów wiersza polecenia do zainstalowania programu Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) strony.  
  
## <a name="specifying-customer-feedback-settings"></a>Określanie ustawień opinii klienta  

Domyślnie instalacja programu Visual Studio umożliwia opinii klientów. Można skonfigurować programu Visual Studio, aby wyłączyć opinie klientów na poszczególnych komputerach, zmieniając wartość następującego klucza rejestru na ciąg "0":  
  
**HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SQM**  
**OptIn**  
  
(Na przykład zmień go na HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SQM OptIn = "0")  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Temat|Opis|  
|-----------|-----------------|  
|[Instrukcje: Instalowanie określonej wersji programu Visual Studio](../install/how-to-install-a-specific-release-of-visual-studio.md)|Opisuje sposób instalowania określonej konfiguracji bieżącą wersję [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|[Instrukcje: Utworzyć i uruchomić nienadzorowaną instalację programu Visual Studio](../install/how-to-create-and-run-an-unattended-installation-of-visual-studio.md)|W tym artykule opisano sposób instalowania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] w trybie nienadzorowanym.|  
|[Instrukcje: Automatyczne stosowanie kluczy produktów podczas wdrażania programu Visual Studio](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md)|Opisuje sposób stosowanie kluczy produktów podczas wdrażania na wielu komputerach.|  
|[Podręcznik administratora programu Podgląd Pomocy](../ide/help-viewer-administrator-guide.md)|Zawiera informacje o sposobie zarządzania lokalnymi instalacjami pomocy dla środowisk sieciowych, które mają lub nie masz dostępu do Internetu.|  
|[Instalowanie programu Visual Studio](../install/install-visual-studio-2015.md)|Zawiera instrukcje i linki do tematów opisujących sposób instalowania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|