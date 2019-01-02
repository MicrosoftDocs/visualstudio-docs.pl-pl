---
title: Wstępnie wymagane składniki — Okno dialogowe
ms.date: 06/29/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.Bootstrapper
helpviewer_keywords:
- Prerequisites dialog box
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e3425573d1ee60ce5a4f96d5762b353afa18dc9b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53827104"
---
# <a name="prerequisites-dialog-box"></a>Wstępnie wymagane składniki — Okno dialogowe

**Wymagania wstępne** okno dialogowe określa, które wstępnie wymagane składniki są zainstalowane, jak są zainstalowane i jakim porządku zainstalowane są pakiety.

![Okno dialogowe wymagań wstępnych w programie Visual Studio](media/prerequisites-dialog-box.png)

Aby otworzyć okno dialogowe, wybierz węzeł projektu w **Eksploratora rozwiązań**, a następnie wybierz pozycję **projektu** > **właściwości**. Gdy **projektanta projektu** pojawi się, wybierz **Publikuj** , a następnie wybierz pozycję **wymagania wstępne**. W przypadku projektów instalacji na **projektu** menu, kliknij przycisk **właściwości**. Gdy **stron właściwości** pojawi się okno dialogowe, kliknij przycisk **wymagania wstępne**.

## <a name="uielement-list"></a>Lista elementów interfejsu użytkownika

|Element|Opis|
|-------------|-----------------|
|**Utwórz program instalacyjny, aby zainstalować wstępnie wymagane składniki**|Obejmuje wstępnie wymagane składniki programu instalacyjnego (*Setup.exe*), dzięki czemu będą one zainstalowane przed aplikacją, w kolejności zależności. Domyślnie ta opcja jest zaznaczona. Jeśli nie jest zaznaczone, nie *Setup.exe* zostanie utworzony.|
|**Wybierz wstępnie wymagane składniki do zainstalowania**|Określa, czy należy zainstalować składniki, takie jak biblioteki środowiska uruchomieniowego .NET Framework i C++.<br /><br />Na przykład przez zaznaczenie pola wyboru obok pozycji **programu SQL Server 2012 Express**, należy określić, że program instalacyjny należy sprawdzić, czy ten składnik jest zainstalowany na komputerze docelowym i zainstaluj go, jeśli nie jest.<br /><br />Aby uzyskać szczegółowe informacje dotyczące każdego pakietu wstępnie wymaganych składników, zobacz [informacje o wymaganiach wstępnych](#prerequisites-information).|
|**Pobierz wstępnie wymagane składniki z witryny dostawcy składników**|Określa, że wstępnie wymagane składniki będą instalowane z witryny internetowej dostawcy. Jest to opcja domyślna.|
|**Pobierz wstępnie wymagane składniki z tej samej lokalizacji co aplikację**|Określa, że wstępnie wymagane składniki będą instalowane z tej samej lokalizacji co aplikacja. To kopiuje wszystkie wstępnie wymagane pakiety do lokalizacji publikowania. Aby opcja działała, składniki muszą się znajdować na komputerze deweloperskim.|
|**Pobierz wstępnie wymagane składniki z następującej lokalizacji**|Określa, że wstępnie wymagane składniki będą instalowane z lokalizacji, do której należy wprowadzić. Możesz użyć **Przeglądaj** przycisk, aby wybrać lokalizację.|

## <a name="prerequisites-information"></a>Informacje o wymaganiach wstępnych

Wstępnie wymagane składniki, które pojawiają się w **wymagania wstępne** okno dialogowe mogą się różnić od tych z poniższej listy. Wstępnie wymagane pakiety wymienione w **wstępnie wymagane składniki, okno dialogowe** są ustawiane automatycznie przy pierwszym otwarciu okna dialogowego. Jeśli użytkownik zmieni później platformę docelową projektu, musisz wybrać wstępnie wymagane składniki ręcznie, aby dopasować do nowej platformy docelowej.

|Element|Opis|
|-------------|-----------------|
|**.NET framework 3.5 z dodatkiem SP1**|Ten pakiet zainstaluje następujące:<br /><br /> — Program .NET framework w wersji 2.0, 3.0 i 3.5.<br />— Obsługuje dla wszystkich wersji .NET Framework na 32-bitowych (x86) i (x64) 64-bitowych systemów operacyjnych.<br />-Pakiety językowe dla każdej wersji .NET Framework, która jest instalowana z pakietem.<br />-Dodatki service Pack dla programu .NET Framework 2.0 i 3.0.<br /><br /> .NET framework 3.0 jest dołączony do Windows Vista i .NET Framework 3.5 jest dołączony do Visual Studio. .NET framework 3.5 jest wymagany dla wszystkich projektów Visual Basic i C#, które są kompilowane dla 32-bitowych systemach operacyjnych i dla którego platforma docelowa jest ustawiona na **.NET Framework 3.5**oraz dla projektów języka Visual Basic i C# dla 64-bitowych systemy operacyjne. (IA64 nie jest obsługiwany.) Należy pamiętać, że projekty języka Visual Basic i C# są kompilowane dla dowolnej architektury Procesora domyślnie. Aby uzyskać więcej informacji, zobacz [Visual Studio Wielowersyjnością kodu – Przegląd](../../ide/visual-studio-multi-targeting-overview.md) i [wdrażanie wstępnie wymaganych składników dla aplikacji 64-bitowych](../../deployment/deploying-prerequisites-for-64-bit-applications.md).|
|**Microsoft .NET Framework 4.x**|Ten pakiet instaluje program .NET Framework 4.x x86 i x64 64.|
|**Program Microsoft System CLR Types dla programu SQL Server 2014 (x64 i x86)**|Ten pakiet zainstaluje Microsoft System CLR Types dla programu SQL Server 2014 dla x64 lub x86.|
|**SQL Server 2008 R2 Express**|Ten pakiet zainstaluje Microsoft SQL Server 2008 R2 Express, bezpłatna wersja programu Microsoft SQL Server 2008 R2, idealną bazę danych dla małych sieci web, serwera lub aplikacji klasycznych. Może służyć do swobodnego rozwoju i produkcji.|
|**SQL Server 2012 Express**|Ten pakiet zainstaluje Microsoft SQL Server 2012 Express.|
|**SQL Server 2012 Express LocalDB**|Ten pakiet zainstaluje Microsoft SQL Server 2012 Express LocalDB.|
|**Visual C++ "14" środowiska uruchomieniowego bibliotek (ARM)**|Ten pakiet instaluje biblioteki Visual C++ środowiska wykonawczego dla architektury Itanium, które zapewniają procedury programowania systemu operacyjnego Microsoft Windows. Te procedury automatyzują wiele typowych zadań programistycznych, które nie są dostarczane przez języki C i C++.<br /><br /> Aby uzyskać więcej informacji, zobacz [odwołanie do biblioteki wykonawczej C](/cpp/c-runtime-library/c-run-time-library-reference).|
|**Visual C++ "14" środowiska uruchomieniowego bibliotek (x64)**|Ten pakiet instaluje biblioteki uruchomieniowe Visual C++ x64 systemów, które zapewniają procedury programowania systemu operacyjnego Microsoft Windows. Te procedury automatyzują wiele typowych zadań programistycznych, które nie są dostarczane przez języki C i C++.<br /><br /> Aby uzyskać więcej informacji, zobacz [odwołanie do biblioteki wykonawczej C](/cpp/c-runtime-library/c-run-time-library-reference).|
|**Visual C++ "14" środowiska uruchomieniowego bibliotek (x86)**|Ten pakiet instaluje biblioteki uruchomieniowe Visual C++ dla x86 systemów, które zapewniają procedury programowania systemu operacyjnego Microsoft Windows. Te procedury automatyzują wiele typowych zadań programistycznych, które nie są dostarczane przez języki C i C++.<br /><br /> Aby uzyskać więcej informacji, zobacz [odwołanie do biblioteki wykonawczej C](/cpp/c-runtime-library/c-run-time-library-reference).|

## <a name="see-also"></a>Zobacz także

- [Strona publikowania, Projektant projektu](../../ide/reference/publish-page-project-designer.md)
- [Wstępnie wymagane składniki wdrażania aplikacji](../../deployment/application-deployment-prerequisites.md)
- [Wdrażanie wstępnie wymaganych składników dla aplikacji 64-bitowych](../../deployment/deploying-prerequisites-for-64-bit-applications.md)
- [Wielowersyjność kodu w programie Visual Studio ― przegląd](../../ide/visual-studio-multi-targeting-overview.md)