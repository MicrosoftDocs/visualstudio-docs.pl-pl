---
title: 'Instrukcje: Rozwiązywanie problemów z usługami | Microsoft Docs'
description: Dowiedz się, jak rozwiązywać kilka typowych problemów, które mogą wystąpić podczas próby uzyskania usługi w zestawie SDK programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f6e29f2c65ec7503f06baca4af4c6772090d5eb8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952294"
---
# <a name="how-to-troubleshoot-services"></a>Instrukcje: Rozwiązywanie problemów z usługami
Istnieje kilka typowych problemów, które mogą wystąpić podczas próby uzyskania usługi:

- Usługa nie jest zarejestrowana w usłudze [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

- Usługa jest zażądana przez typ interfejsu, a nie za pomocą typu usługi.

- Pakietu VSPackage żądający usługi nie został zlokalizowany.

- Używany jest niewłaściwy dostawca usług.

  Jeśli żądana usługa nie może zostać uzyskana, wywołanie <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> zwraca wartość null. Należy zawsze testować pod kątem wartości null po zażądaniu usługi:

```csharp
IVsActivityLog log =
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="to-troubleshoot-a-service"></a>Aby rozwiązać problemy z usługą

1. Sprawdź rejestr systemu, aby sprawdzić, czy usługa została prawidłowo zarejestrowana. Aby uzyskać więcej informacji, zobacz [How to: zapewnianie usługi](../extensibility/how-to-provide-a-service.md).

    Poniższy fragment pliku *reg* zawiera informacje o tym, jak usługa SVsTextManager może być zarejestrowana:

   ```
   [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]
   @="{F5E7E720-1401-11d1-883B-0000F87579D2}"
   "Name"="SVsTextManager"
   ```

    W powyższym przykładzie numer wersji to wersja programu, na przykład [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 12,0 lub 14,0, klucz {F5E7E71D-1401-11D1-883B-0000F87579D2} to identyfikator usługi (SID) usługi, SVsTextManager i wartość domyślna {F5E7E720-1401-11D1-883B-0000F87579D2} to identyfikator GUID pakietu pakietu vspackageego Menedżera tekstu, który udostępnia usługę.

2. Użyj typu usługi, a nie typu interfejsu podczas wywoływania metody GetService. Podczas żądania usługi z programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] program <xref:Microsoft.VisualStudio.Shell.Package> wyodrębnia identyfikator GUID z typu. Usługa nie zostanie znaleziona, jeśli istnieją następujące warunki:

   1. Typ interfejsu jest przesyłany do elementu GetService zamiast typu usługi.

   2. Żaden identyfikator GUID nie jest jawnie przypisany do interfejsu. W związku z tym system tworzy domyślny identyfikator GUID dla obiektu w razie potrzeby.

3. Upewnij się, że pakietu VSPackage żądający usługi został zlokalizowany. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Lokacje a pakietu VSPackage po utworzeniu i przed wywołaniem <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> .

    Jeśli masz kod w konstruktorze pakietu VSPackage, który wymaga usługi, przenieś ją do `Initialize` metody.

4. Upewnij się, że używasz poprawnego dostawcy usług.

    Nie wszyscy dostawcy usług są podobne. Dostawca usług, który [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] przechodzi do okna narzędzi, różni się od tego, który przekazuje do pakietu VSPackage. Dostawca usługi okna narzędzi wie o tym <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> , ale nie wie o tym <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> . Możesz wywołać, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> Aby uzyskać dostawcę usług pakietu VSPackage z poziomu okna narzędzi.

    Jeśli okno narzędzi hostuje kontrolkę użytkownika lub inny kontener sterowania, kontener będzie zlokalizowany przez model składników systemu Windows i nie będzie miał dostępu do żadnych [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] usług. Możesz wywołać, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> Aby uzyskać dostawcę usług pakietu VSPackage z poziomu kontenera kontroli.

## <a name="see-also"></a>Zobacz też
- [Lista dostępnych usług](../extensibility/internals/list-of-available-services.md)
- [Używanie i udostępnianie usług](../extensibility/using-and-providing-services.md)
- [Podstawowa usługa](../extensibility/internals/service-essentials.md)
- [Rozwiązywanie problemów z programem Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)