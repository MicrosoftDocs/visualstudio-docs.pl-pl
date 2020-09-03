---
title: Jak zweryfikować ustawienia właściwości usług IIS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- IIS, property settings
- debugging Web applications, troubleshooting
- IIS administration tool
- Web applications, setting properties
- properties [debugger], setting with IIS administration tool
ms.assetid: 9efc50bf-02fb-4750-9b3e-f03c38f10d8b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f37a1ee196b14ec1f8c7b03ffc6e6d826ced02d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85348473"
---
# <a name="how-to-verify-iis-property-settings"></a>Porady: weryfikacja właściwości ustawień IIS

Możesz ustawić właściwości aplikacji sieci Web za pomocą narzędzia administracyjnego usług IIS. Aby można było uruchomić aplikację, te właściwości muszą być poprawnie skonfigurowane, co oznacza, że te ustawienia często są niezbędne do rozwiązywania problemów.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Resetowanie ustawień](../ide/environment-settings.md#reset-settings).

## <a name="to-check-iis-settings-for-the-web-application"></a>Aby sprawdzić ustawienia usług IIS dla aplikacji sieci Web

1. Otwórz okno **Narzędzia administracyjne** : w menu **Start** wskaż pozycję **programy**, a następnie kliknij pozycję **Narzędzia administracyjne**. Jeśli **Narzędzia administracyjne** nie są wyświetlane w menu **programy** , wyszukaj je w **Panelu sterowania**.

   - W systemie Windows 2000 wybierz pozycję **Menedżer usług internetowych**.

   - W systemie Windows XP wybierz pozycję **Internet Information Services**.

   - W systemie Windows Server 2003 kliknij dwukrotnie pozycję **Zarządzanie serwerem**.

        Zostanie otwarte okno **Zarządzanie serwerem** . W obszarze **serwer aplikacji**kliknij pozycję **Zarządzaj tym serwerem aplikacji**.

        Zostanie otwarte okno **serwer aplikacji** . Otwórz węzeł **menedżer Internet Information Services (IIS)** w okienku po lewej stronie.

2. W oknie dialogowym kliknij węzeł kontrolki drzewa dla komputera. Kliknij węzeł **witryny sieci Web** , a następnie wybierz węzeł aplikacji sieci Web. Będzie to węzeł witryny sieci Web, a więc element równorzędny **domyślnego węzła witryny sieci Web** lub węzeł katalogu wirtualnego znajdujący się pod istniejącym węzłem witryny sieci Web.

3. Kliknij prawym przyciskiem myszy aplikację sieci Web, a następnie w menu skrótów kliknij polecenie **Właściwości**.

4. Sprawdź ustawienia zabezpieczeń aplikacji sieci Web:

   1. W oknie **Właściwości** aplikacji sieci Web kliknij kartę **Zabezpieczenia katalogów** , a następnie kliknij przycisk **Edytuj**.

   2. W oknie dialogowym **metody uwierzytelniania** wybierz opcję **Włącz dostęp anonimowy** i **zintegrowane uwierzytelnianie systemu Windows** , jeśli nie zostały jeszcze wybrane.

   3. Kliknij przycisk **OK** , aby zamknąć okno dialogowe **metody uwierzytelniania** .

5. W przypadku aplikacji serwera ATL upewnij się, że zlecenie debugowania jest skojarzone z rozszerzeniem ISAPI. Aby uzyskać więcej informacji, zobacz [How to: Skojarz CZASOWNIK Debug with Extension](https://msdn.microsoft.com/library/50d261d3-4bd4-41c0-b44e-3591086f121e).

6. W przypadku [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji upewnij się, że folder wirtualny aplikacji ma ustawioną nazwę aplikacji w **Menedżerze Internet Information Services (IIS)**, **Menedżer usług internetowych** lub **Internet Information Services**.

   1. W oknie **Właściwości** aplikacji sieci Web wybierz kartę **katalog** , jeśli aplikacja znajduje się w katalogu wirtualnym lub na karcie **katalog macierzysty** , jeśli aplikacja znajduje się w witrynie sieci Web.

   2. Sprawdź, czy nazwa w **ścieżce lokalnej** jest zgodna z nazwą katalogu, w którym aplikacja została faktycznie wdrożona.

   3. W obszarze **Ustawienia aplikacji**wpisz nazwę katalogu głównego, który zawiera aplikację.

   4. Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Właściwości** .

7. W przypadku [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji kliknij kartę **ASP.NET** i sprawdź, czy została określona poprawna wersja programu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] .

8. Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Właściwości** .

9. Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Internet Information Services (IIS) menedżer** **Menedżer usług internetowych**lub **Internet Information Services** .

## <a name="see-also"></a>Zobacz też

- [Rozwiązywanie problemów](../debugger/debugging-web-applications-troubleshooting.md)