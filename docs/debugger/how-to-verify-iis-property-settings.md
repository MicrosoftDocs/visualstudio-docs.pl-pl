---
title: 'Instrukcje: Sprawdź właściwości ustawień usług IIS | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 3dd516151f7a3656da1bae195870e8cc29528cfa
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60075249"
---
# <a name="how-to-verify-iis-property-settings"></a>Instrukcje: Weryfikacja właściwości ustawień IIS

Można ustawić właściwości dla aplikacji sieci Web za pomocą narzędzia administracyjnego IIS. Te właściwości muszą być ustawione poprawnie dla aplikacji do uruchomienia, więc weryfikowanie tych ustawień jest często konieczne etapem rozwiązywania problemów.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [zresetować ustawienia](../ide/environment-settings.md#reset-settings).

## <a name="to-check-iis-settings-for-the-web-application"></a>Aby sprawdzić ustawienia usług IIS dla aplikacji sieci Web

1. Otwórz **narzędzia administracyjne** okna: Na **Start** menu wskaż **programy**, a następnie kliknij przycisk **narzędzia administracyjne**. Jeśli **narzędzia administracyjne** nie jest widoczna w **programy** menu, a następnie wyszukaj go w **Panelu sterowania**.

   - W systemie operacyjnym Windows 2000, wybierz **Menedżera internetowych usług**.

   - Windows XP, należy wybrać **Internetowe usługi informacyjne**.

   - W systemie Windows Server 2003, kliknij dwukrotnie **Zarządzanie serwerem**.

        **Zarządzanie serwerem** zostanie otwarte okno. W obszarze **serwera aplikacji**, kliknij przycisk **zarządzać tym serwerem aplikacji**.

        **Serwera aplikacji** zostanie otwarte okno. Otwórz **Internet Information Services (IIS) Manager** węzła w okienku po lewej stronie.

2. W oknie dialogowym kliknij węzeł formantu drzewa dla maszyny. Kliknij przycisk **witryn sieci Web** węzeł i wybierz węzeł, aplikacji sieci Web. To będzie węzeł witryny sieci Web, a tym samym elementem równorzędnym węzła **domyślna witryna sieci Web** , lub węzeł katalogu wirtualnego, poniżej istniejący węzeł witryny sieci Web.

3. Kliknij prawym przyciskiem myszy aplikację sieci Web, a następnie w menu skrótów kliknij **właściwości**.

4. Sprawdź ustawienia zabezpieczeń dla aplikacji sieci Web:

   1. W aplikacji sieci Web **właściwości** okna, kliknij przycisk **zabezpieczeń katalogu** kartę, a następnie kliknij przycisk **Edytuj**.

   2. W **metod uwierzytelniania** okno dialogowe, wybierz opcję **Włącz dostęp anonimowy** i **uwierzytelniania zintegrowanego Windows** Jeśli nie są jeszcze wybrane.

   3. Kliknij przycisk **OK** zamknąć **metod uwierzytelniania** okno dialogowe.

5. Dla aplikacji serwera ATL. Sprawdź, czy czasownik DEBUG jest skojarzony z rozszerzenia ISAPI. Aby uzyskać więcej informacji, zobacz [jak: Skojarz czasownik DEBUG z rozszerzeniem](https://msdn.microsoft.com/library/50d261d3-4bd4-41c0-b44e-3591086f121e).

6. Aby uzyskać [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji, sprawdź folder wirtualny dla aplikacji ma nazwę aplikacji w **Menedżera usług Internet Information Services (IIS)**, **Menedżera internetowych usług** lub  **Internetowe usługi informacyjne**.

   1. W aplikacji sieci Web **właściwości** wybierz **katalogu** kartę, jeśli aplikacja znajduje się w katalogu wirtualnym lub **katalog macierzysty** kartę, jeśli aplikacja znajduje się w Witryna sieci Web.

   2. Upewnij się, że nazwa w **ścieżkę lokalną** jest zgodna z nazwą katalogu, w którym aplikacja została faktycznie wdrożona.

   3. W obszarze **ustawienia aplikacji**, wpisz nazwę katalogu głównego, który zawiera aplikację.

   4. Kliknij przycisk **OK** zamknąć **właściwości** okno dialogowe.

7. Dla [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji, kliknij przycisk **ASP.NET** kartę i sprawdź, czy poprawną wersję [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] jest określony.

8. Kliknij przycisk **OK** zamknąć **właściwości** okno dialogowe.

9. Kliknij przycisk **OK** zamknąć **Internet Information Services (IIS) Manager**, **Menedżera usług internetowych**, lub **Internetowe usługi informacyjne**okno dialogowe.

## <a name="see-also"></a>Zobacz także

- [Rozwiązywanie problemów](../debugger/debugging-web-applications-troubleshooting.md)