---
title: '&lt;trustInfo&gt; — Element (aplikacja ClickOnce) | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#IPermission
- urn:schemas-microsoft-com:asm.v2#PermissionSet
- urn:schemas-microsoft-com:asm.v2#assemblyRequest
- urn:schemas-microsoft-com:asm.v2#trustInfo
- urn:schemas-microsoft-com:asm.v2#defaultAssemblyRequest
- urn:schemas-microsoft-com:asm.v2#security
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- manifests [ClickOnce], trustInfo element
- <trustInfo> element [ClickOnce application manifest]
ms.assetid: 8a813a74-e158-4308-be78-565937f6af83
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ca7e19925288b1509fec08235f546b84b4afffef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62420086"
---
# <a name="lttrustinfogt-element-clickonce-application"></a>&lt;trustInfo&gt; — Element (aplikacja ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Opisuje minimalne uprawnienia zabezpieczeń wymagane do zastosowania do uruchomienia na komputerze klienckim.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      <trustInfo>  
   <security>  
      <applicationRequestMinimum>  
         <PermissionSet  
            ID  
            Unrestricted>  
            <IPermission  
               class  
               version  
               Unrestricted  
            />  
         </PermissionSet>  
         <defaultAssemblyRequest  
            permissionSetReference  
         />  
         <assemblyRequest  
            name  
            permissionSetReference  
         />  
      </applicationRequestMinimum>  
      <requestedPrivileges>  
         <requestedExecutionLevel  
            level  
            uiAccess  
         />  
      </requestedPrivileges>  
   </security>  
</trustInfo>  
```  
  
## <a name="elements-and-attributes"></a>Atrybuty i elementy  
 `trustInfo` Element jest wymagany i znajduje się w `asm.v2` przestrzeni nazw. Go nie ma żadnych atrybutów i zawiera następujące elementy.  
  
## <a name="security"></a>zabezpieczenia  
 Wymagana. Ten element jest elementem podrzędnym `trustInfo` elementu. Zawiera on `applicationRequestMinimum` elementu i nie ma żadnych atrybutów.  
  
## <a name="applicationrequestminimum"></a>applicationRequestMinimum  
 Wymagana. Ten element jest elementem podrzędnym `security` elementu i zawiera `PermissionSet`, `assemblyRequest`, i `defaultAssemblyRequest`elementów. Ten element nie ma żadnych atrybutów.  
  
## <a name="permissionset"></a>PermissionSet  
 Wymagana. Ten element jest elementem podrzędnym `applicationRequestMinimum` elementu i zawiera `IPermission` elementu. Ten element ma następujące atrybuty.  
  
- `ID`  
  
     Wymagana. Identyfikuje zestaw uprawnień. Ten atrybut może być dowolna wartość. Identyfikator jest przywoływany w `defaultAssemblyRequest` i `assemblyRequest` atrybutów.  
  
- `version`  
  
     Wymagana. Identyfikuje wersję uprawnienia. Ta wartość jest zazwyczaj `1`.  
  
## <a name="ipermission"></a>Interfejsu IPermission  
 Opcjonalna. Ten element jest elementem podrzędnym `PermissionSet` elementu. `IPermission` Elementu pełni identyfikuje klasy uprawnień w [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. `IPermission` Element ma następujące atrybuty, ale mogą mieć dodatkowe atrybuty, które odnoszą się do właściwości klasy uprawnień. Aby sprawdzić składnię określone uprawnienie, zobacz temat w przykładach wymienionych w pliku Security.config —.  
  
- `class`  
  
     Wymagana. Identyfikuje klasy uprawnień za pomocą silnej nazwy. Na przykład, poniższy kod określa `FileDialogPermission` typu.  
  
     `System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
- `version`  
  
     Wymagana. Identyfikuje wersję uprawnienia. Ta wartość jest zazwyczaj `1`.  
  
- `Unrestricted`  
  
     Wymagana. Określa, czy aplikacja musi nieograniczony przyznanie tego uprawnienia. Jeśli `true`, udzielenia uprawnień to bezwarunkowy. Jeśli `false`, lub jeśli ten atrybut jest niezdefiniowana, jest ograniczona zgodnie z atrybutów określonych uprawnień wobec `IPermission` tagu. Wykonaj następujące uprawnienia:  
  
    ```  
    <IPermission  
      class="System.Security.Permissions.EnvironmentPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
      version="1"   
      Read="USERNAME" />  
    <IPermission  
      class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
      version="1"   
      Unrestricted="true" />  
    ```  
  
     W tym przykładzie deklaracji pod kątem <xref:System.Security.Permissions.EnvironmentPermission> ogranicza aplikacji do odczytywania tylko zmienna środowiskowa USERNAME, natomiast deklaracji pod kątem <xref:System.Security.Permissions.FileDialogPermission> zapewnia użytkowania aplikacji bez ograniczeń, wszystkie <xref:System.Windows.Forms.FileDialog> klasy.  
  
## <a name="defaultassemblyrequest"></a>defaultAssemblyRequest  
 Opcjonalna. Identyfikuje zestaw wszystkich zestawów uprawnień. Ten element jest elementem podrzędnym `applicationRequestMinimum` elementu i ma następujący atrybut.  
  
- `permissionSetReference`  
  
     Wymagana. Określa identyfikator zestawu uprawnień, który jest domyślnym uprawnieniem. Zestaw uprawnień jest zadeklarowana w `PermissionSet` elementu.  
  
## <a name="assemblyrequest"></a>assemblyRequest  
 Opcjonalna. Umożliwia określenie uprawnień dla określonego zestawu. Ten element jest elementem podrzędnym `applicationRequestMinimum` elementu i ma następujące atrybuty.  
  
- `Name`  
  
     Wymagana. Określa nazwę zestawu.  
  
- `permissionSetReference`  
  
     Wymagana. Określa identyfikator zestawu uprawnień, który wymaga tego zestawu. Zestaw uprawnień jest zadeklarowana w `PermissionSet` elementu.  
  
## <a name="requestedprivileges"></a>requestedPrivileges  
 Opcjonalna. Ten element jest elementem podrzędnym `security` elementu i zawiera `requestedExecutionLevel` elementu. Ten element nie ma żadnych atrybutów.  
  
## <a name="requestedexecutionlevel"></a>requestedExecutionLevel  
 Opcjonalna. Określa poziom zabezpieczeń, w którym aplikacja żąda wykonania. Ten element nie ma elementów podrzędnych i ma następujące atrybuty.  
  
- `Level`  
  
     Wymagana. Wskazuje, że żąda poziomu zabezpieczeń aplikacji. Możliwe wartości to:  
  
     `asInvoker`, żądanie żadne dodatkowe uprawnienia. Ten poziom nie wymaga żadnych dodatkowych zaufania wyświetla monit o.  
  
     `highestAvailable`, żąda uprawnienia najwyższy dostępny dla procesu nadrzędnego.  
  
     `requireAdministrator`, żąda uprawnienia administrator o pełnych uprawnieniach.  
  
     [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacje będą instalowane tylko z wartością `asInvoker`. Instalowanie przy użyciu dowolnej innej wartości zakończy się niepowodzeniem.  
  
- `uiAccess`  
  
     Opcjonalna. Wskazuje, czy aplikacja wymaga dostępu do elementów interfejsu użytkownika chronionych. Wartości są albo `true` lub `false`, a wartość domyślna to false. Tylko podpisane aplikacje powinny mieć wartość true.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacja prosi o więcej uprawnień niż przyzna komputer kliencki domyślnie języka wspólnego, Menedżer zaufania środowiska uruchomieniowego będzie monitować użytkownika, jeśli chce udzielić aplikacji tym podwyższonego poziomu zaufania. Jeśli jest ona w stanie nie, aplikacja nie zostanie uruchomiona; w przeciwnym razie zostaną uruchomione żądane uprawnienia.  
  
 Wszystkie uprawnienia żądana za pomocą `defaultAssemblyRequest` i `assemblyRequest` zostaną przyznane bez monitowania użytkownika, jeśli manifest wdrożenia ma prawidłową licencję zaufania.  
  
 Aby uzyskać więcej informacji o podniesienie uprawnień, zobacz [zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md). Aby uzyskać więcej informacji na temat wdrażania zasad, zobacz [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
## <a name="examples"></a>Przykłady  
 W poniższych przykładach kodu trzy pokazano `trustInfo` elementów domyślnego o nazwie strefy zabezpieczeń — Internet, LocalIntranet i FullTrust — do użytku w [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożenia manifest aplikacji.  
  
 W pierwszym przykładzie pokazano `trustInfo` elementu domyślne uprawnienia dostępne w strefie zabezpieczeń Internet.  
  
```  
<trustInfo>  
    <security>  
      <applicationRequestMinimum>  
        <PermissionSet ID="Internet">  
          <IPermission  
            class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
            version="1"   
            Access="Open" />  
          <IPermission  
           class="System.Security.Permissions.IsolatedStorageFilePermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"  
            Allowed="DomainIsolationByUser"  
            UserQuota="10240" />  
          <IPermission  
            class="System.Security.Permissions.SecurityPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
            version="1"   
            Flags="Execution" />  
          <IPermission   
            class="System.Security.Permissions.UIPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Window="SafeTopLevelWindows"  
            Clipboard="OwnClipboard" />  
          <IPermission  
            class="System.Drawing.Printing.PrintingPermission, System.Drawing, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"  
            version="1"   
            Level="SafePrinting" />  
        </PermissionSet>  
        <defaultAssemblyRequest permissionSetReference="Internet" />  
      </applicationRequestMinimum>  
    </security>  
  </trustInfo>  
```  
  
 Drugi przykład przedstawia `trustInfo` elementu domyślne uprawnienia dostępne w strefie zabezpieczeń LocalIntranet.  
  
```  
<trustInfo>  
    <security>  
      <applicationRequestMinimum>  
        <PermissionSet ID="LocalIntranet">  
          <IPermission  
            class="System.Security.Permissions.EnvironmentPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Read="USERNAME" />  
          <IPermission  
            class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Unrestricted="true" />  
          <IPermission  
            class="System.Security.Permissions.IsolatedStorageFilePermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Allowed="AssemblyIsolationByUser"  
            UserQuota="9223372036854775807"  
            Expiry="9223372036854775807"  
            Permanent="True" />  
          <IPermission  
            class="System.Security.Permissions.ReflectionPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Flags="ReflectionEmit" />  
          <IPermission  
            class="System.Security.Permissions.SecurityPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Flags="Assertion, Execution" />  
          <IPermission   
            class="System.Security.Permissions.UIPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
            version="1"   
            Unrestricted="true" />  
          <IPermission  
            class="System.Net.DnsPermission, System, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
            version="1"   
            Unrestricted="true" />  
          <IPermission  
            class="System.Drawing.Printing.PrintingPermission, System.Drawing, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"  
            version="1"  
            Level="DefaultPrinting" />  
          <IPermission  
            class="System.Diagnostics.EventLogPermission, System, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
            version="1" />  
        </PermissionSet>  
        <defaultAssemblyRequest permissionSetReference="LocalIntranet" />  
      </applicationRequestMinimum>  
    </security>  
</trustInfo>  
```  
  
 Trzeci przykład ilustruje `trustInfo` elementu domyślne uprawnienia dostępne w strefie zabezpieczeń FullTrust.  
  
```  
<trustInfo>  
  <security>  
    <applicationRequestMinimum>  
      <PermissionSet ID="FullTrust" Unrestricted="true" />  
      <defaultAssemblyRequest permissionSetReference="FullTrust" />  
    </applicationRequestMinimum>  
  </security>  
</trustInfo>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md)   
 [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)
