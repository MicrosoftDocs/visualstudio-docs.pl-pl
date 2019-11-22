---
title: Przewodnik administratora programu Visual Studio | Microsoft Docs
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
ms.openlocfilehash: a59f9f2cb2548d6d40670832e66d4df5c83680df
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295924"
---
# <a name="visual-studio-administrator-guide"></a>Podręcznik administratora programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio, zobacz [Podręcznik administratora programu Visual Studio](/visualstudio/install/visual-studio-administrator-guide).

Program Visual Studio 2015 można wdrożyć w sieci, o ile każdy komputer docelowy spełnia [minimalne wymagania dotyczące instalacji](https://visualstudio.microsoft.com/vs/older-downloads/). Udział sieciowy można utworzyć, uruchamiając plik instalacyjny z przełącznikiem/Layout (zgodnie z opisem na stronie [Tworzenie instalacji w trybie offline programu Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) ), a następnie kopiując go z komputera lokalnego do udziału sieciowego. W przypadku korzystania z obrazu ISO można zainstalować ISO i udostępnić go lub skopiować plik ISO do udziału sieciowego.  
  
 Należy pamiętać, że instalacje z udziału sieciowego "Pamiętaj" lokalizację źródłową, z której pochodzą. Oznacza to, naprawy maszyny klienta może być konieczne powrócić do udziału sieciowego, który pierwotnie zainstalowany klient z. Należy uważnie wybrać swoją lokalizację sieciową, aby wyrównać okres istnienia, w którym ma być uruchomiony klient programu Visual Studio 2015 w organizacji.  
  
## <a name="detection-and-servicing-keys"></a>Klucze wykrywania i obsługi  
 Aby określić, czy produkt Visual Studio jest już zainstalowany na komputerze, można użyć w rejestrze podkluczy wykrywania. Te klucze wykrywania można użyć w zautomatyzowanym wdrożeniu, aby określić, czy było wymagane przeprowadzenie instalacji.  Zobacz [wykrywanie wymagań systemowych](../extensibility/internals/detecting-system-requirements.md)[wykrywanie wymagań systemowych].  
  
## <a name="avoiding-reboots"></a>Unikanie ponownego uruchamiania  
 Aby zmniejszyć liczbę ponownych uruchomień, należy upewnić się, że spełniasz odpowiednie wymagania wstępne programu Visual Studio przed wdrożeniem programu Visual Studio. W przypadku .NET Framework może być konieczne ponowne uruchomienie komputerów z systemem Windows 8 w przypadku wdrożenia na nich programu Visual Studio 2015 bez wcześniejszego zainstalowania .NET Framework 4,6.  
  
 W przypadku emulacji urządzeń z systemami Windows i Android może być konieczne ponowne uruchomienie komputera, jeśli nie jest jeszcze włączona funkcja Hyper-V systemu Windows. W przypadku programowania w sieci Web może być konieczne ponowne uruchomienie komputera, jeśli nie jest jeszcze włączony serwer sieci Web funkcji systemu Windows. W przypadku tworzenia pakietu Office może być konieczne ponowne uruchomienie komputera, jeśli nie masz jeszcze włączonej funkcji Windows system Windows Zidentyfikuj podstawę. ponownie uruchom komputery, jeśli nie masz jeszcze włączonego serwera sieci Web funkcji systemu Windows. W przypadku tworzenia pakietu Office może być konieczne ponowne uruchomienie komputera, jeśli nie masz jeszcze włączonej funkcji Windows system Windows Zidentyfikuj podstawę. Aby dowiedzieć się więcej o automatyzowaniu wykrywania i instalacji funkcji systemu Windows, zobacz [Instalowanie roli serwera na serwerze z instalacją Server Core systemu Windows server 2008 R2](https://technet.microsoft.com/library/ee441260(v=ws.10).aspx).  
  
## <a name="error-return-codes"></a>Kody powrotu błędu  
 Poniższa tabela zawiera listę ważnych kodów błędów. Możesz użyć tych kodów błędów w usłudze Automation, aby zdecydować, czy jest wymagany ponowny rozruch i czy instalacja zakończyła się pomyślnie. Jeśli zostanie wyświetlony kod błędu, należy rozważyć kroki rozwiązywania problemów na stronie [Instalowanie programu Visual Studio](../install/install-visual-studio-2015.md) .  
  
|Stan instalacji|Ponowne uruchomienie nie jest wymagane|Wymagane ponowne uruchomienie|Opis|  
|------------------|--------------------------|----------------------|-----------------|  
|Powodzenie|0x00000000 [0]|0x00000bc2 [3010]|Instalacja powiodła się.|  
|Blokuj|0x80044000 [-2147205120]|0x8004C000 [-2147172352]|Jeśli jedyny blok do zgłoszenia to "Oczekiwanie na ponowne uruchomienie," zwrócona wartość to wymagana wartość nieukończonego ponownego rozruchu (0x80048bc7).|  
|Anuluj|0x00000642 [1602]|0x80048642 [-2147187134]|Gdy zostanie zwrócona wartość ponownego uruchomienia, kod powrotny to 1602.|  
|Niekompletne — wymagane ponowne uruchomienie komputera|Brak|0x80048bc7 [-2147185721]|Przed kontynuowaniem instalacji wymagane jest ponowne uruchomienie.|  
|Spraw|0x00000643 [1603]|0x80048643 [-2147187133]|Gdy zostanie zwrócona wartość ponownego uruchomienia, kod powrotny to 1603.|  
  
## <a name="interactive-administrator-installer"></a>Instalator administratora interakcyjnego  
 Jeśli tworzysz Instalator interaktywny na bazie instalacji programu Visual Studio, możesz wyświetlić postęp z Instalatora programu Visual Studio. Instalator programu Visual Studio 2015 jest oparty na technologii łańcucha WiX (Open Instalator Windows Source) w sieci, znanej także pod nazwą "wypalanie". Technologia nagrywania obsługuje dwa protokoły komunikacyjne: nagrywanie i netfx4. Zwięzłe odwołanie można znaleźć w opisie atrybutu Protocol w dokumentacji elementu ExePackage w [wixtoolset.org](https://wixtoolset.org/). Przegląd implementacji WiX Open Source tego atrybutu protokołu może być wymagany do integracji.  
  
## <a name="controlling-what-is-installed"></a>Kontrolowanie, co jest zainstalowane  
 Jeśli chcesz kontrolować, co użytkownik końcowy może zainstalować, dostępne są dwie opcje: Instalacja pliku administratora i opcje wiersza polecenia. Wybierz opcję Zainstaluj plik administratora, jeśli zamierzasz ograniczyć możliwości wybranych przez użytkownika końcowego do pracy z instalatorem programu Visual Studio. Wybierz parametry wiersza polecenia, jeśli chcesz utworzyć początkową konfigurację, ale zezwolić użytkownikom końcowym na wybór własnego środowiska Instalatora programu Visual Studio.  
  
 Aby uzyskać więcej informacji na temat środowiska plików administratora, zobacz [How to: Create and run a Unattended Installation of Visual Studio](../install/how-to-create-and-run-an-unattended-installation-of-visual-studio.md) i [instrukcje: automatyczne stosowanie kluczy produktów podczas wdrażania programu Visual Studio](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md).  Aby uzyskać więcej informacji na temat kontrolek wiersza polecenia, zobacz stronę [Używanie parametrów wiersza polecenia do instalowania programu Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) .  
  
## <a name="specifying-customer-feedback-settings"></a>Określanie ustawień opinii klientów  

Domyślnie instalacja programu Visual Studio umożliwia opinii klientów. Można skonfigurować program Visual Studio, aby wyłączyć Opinie klientów na poszczególnych komputerach, zmieniając wartość następującego klucza rejestru na ciąg "0":  
  
**HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SQM**  
**OptIn**  
  
(Na przykład zmień go na HKEY_LOCAL_MACHINE \SOFTWARE\Policies\Microsoft\VisualStudio\SQM OptIn powoduje = "0")  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Temat|Opis|  
|-----------|-----------------|  
|[Instrukcje: instalowanie określonej wersji programu Visual Studio](../install/how-to-install-a-specific-release-of-visual-studio.md)|Opisuje sposób instalowania określonych konfiguracji bieżącej wersji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|[Instrukcje: tworzenie i uruchamianie nienadzorowanej instalacji programu Visual Studio](../install/how-to-create-and-run-an-unattended-installation-of-visual-studio.md)|Opisuje sposób instalowania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] w trybie nienadzorowanym.|  
|[Instrukcje: automatyczne stosowanie kluczy produktów podczas wdrażania programu Visual Studio](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md)|Opisuje sposób stosowania kluczy produktów podczas wdrażania na wielu maszynach.|  
|[Podręcznik administratora programu Podgląd Pomocy](../ide/help-viewer-administrator-guide.md)|Zawiera informacje o sposobach zarządzania lokalnymi instalacjami pomocy dla środowisk sieciowych, które mają lub nie mają dostępu do Internetu.|  
|[Instalowanie programu Visual Studio](../install/install-visual-studio-2015.md)|Zawiera instrukcje i linki do tematów opisujących sposób instalowania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|