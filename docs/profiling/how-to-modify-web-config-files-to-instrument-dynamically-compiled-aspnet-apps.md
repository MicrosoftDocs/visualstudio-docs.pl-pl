---
title: 'Plik Web.Config: Instrument & profil dynamiczny skompilowany ASP.NET aplikacji internetowej'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a92e5692-2183-4ae3-9431-b067c6a7aab4
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 6fb67a5b0da186bd87b9e5c39204e3acccc0529f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74775411"
---
# <a name="how-to-modify-webconfig-files-to-instrument-and-profile-dynamically-compiled-aspnet-web-applications"></a>Jak: Modyfikowanie plików web.config do instrumentów i profilów dynamicznie skompilowanych ASP.NET aplikacji internetowych
Za pomocą [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] metody instrumentacji Narzędzia profilowania można zbierać szczegółowe dane chronometrażu, dane alokacji [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pamięci .NET i dane okresu istnienia obiektu .NET z dynamicznie skompilowanych aplikacji sieci Web.

 W tym temacie opisano sposób modyfikowania pliku konfiguracyjnego *web.config* w celu włączenia instrumentacji i profilowania aplikacji [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] sieci Web.

> [!NOTE]
> Nie jest wymagane modyfikowanie pliku *web.config* podczas korzystania z metody profilowania próbkowania lub [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] gdy chcesz przyrządzać wstępnie skompilowany moduł.

 Katalog główny pliku *web.config* jest elementem **konfiguracji.** Aby zainstruować i [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] profilować dynamicznie skompilowaną aplikację internetową, należy dodać lub zmodyfikować następujące elementy:

- Element **configuration/runtime/assemblyBinding/dependentAssembly** identyfikujący zestaw Microsoft.VisualStudio.Enterprise.ASPNetHelper sterujący profilowaniem. Element **dependentAssembly** zawiera dwa elementy podrzędne: **assemblyIdentity** i **codeBase**.

- Element **configuration/system.web/compilation** identyfikujący krok kompilacji poprocesowej profilera dla zestawu docelowego.

- Dwa **elementy dodawania** identyfikujące lokalizację narzędzi narzędzi narzędzi profilowania są dodawane do sekcji **konfiguracja/appSettings** .

  Zaleca się utworzenie kopii oryginalnego pliku *web.config,* którego można użyć do przywrócenia konfiguracji aplikacji.

### <a name="to-add-the-aspnethelper-assembly-as-a-configurationruntimeassemblybindingdependentassembly-element"></a>Aby dodać zestaw ASPNetHelper jako element konfiguracja/środowisko wykonawcze/assemblyBinding/dependentAssembly

1. W razie potrzeby dodaj element **środowiska wykonawczego** jako element podrzędny elementu **konfiguracji;** w przeciwnym razie przejdź do następnego kroku.

    Element **środowiska wykonawczego** nie ma żadnych atrybutów. Element **konfiguracji** może mieć tylko jeden element **podrzędny środowiska uruchomieniowego.**

2. Jeśli to konieczne, dodaj **element assemblyBinding** jako element podrzędny elementu **środowiska wykonawczego;** w przeciwnym razie przejdź do następnego kroku.

    Element **środowiska wykonawczego** może mieć tylko jeden element **zestawuBinowanie.**

3. Dodaj następującą nazwę atrybutu i wartość do **elementu zestawuBinowanie:**

   | Nazwa atrybutu | Wartość atrybutu |
   |----------------|--------------------------------------|
   | **Xmlns** | **urn:schemas-microsoft-com:asm.v1** |

4. Dodaj **zależnyAszeby** element jako element podrzędny **elementu assemblyBinding.**

    Element **dependentAssembly** nie ma żadnych atrybutów.

5. Dodaj **element assemblyIdentity** jako element podrzędny **elementu dependentAssembly.**

6. Dodaj następujące nazwy atrybutów i wartości do **elementu assemblyIdentity:**

   | Nazwa atrybutu | Wartość atrybutu |
   |--------------------| - |
   | **Nazwa** | **Microsoft.VisualStudio.Enterprise.ASPNetHelper** |
   | **Publickeytoken** | **b03f5f7f11d50a3a** |
   | **kultura** | **Neutral** |

7. Dodaj **element codeBase** jako element podrzędny **elementu dependentAssembly.**

8. Dodaj następujące nazwy atrybutów i wartości do elementu **codeBase:**

   |Nazwa atrybutu|Wartość atrybutu|
   |--------------------|---------------------|
   |**Wersja**|**10.0.0.0**|
   |**Href**|`PathToASPNetHelperDll`|

    `PathToASPNetHelperDll`jest adresem URL pliku pliku Microsoft.VisualStudio.Enterprise.ASPNetHelper.dll. Jeśli [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jest zainstalowany w lokalizacji domyślnej, wartość **href** powinna być`C:/Program%20Files/Microsoft%20Visual%20Studio%202010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL`

```xml
    <configuration>
        <runtime>
            <assemblyBinding
                xmlns="urn:schemas-microsoft-com:asm.v1"
            >
                <dependentAssembly>
                    <assemblyIdentity name="Microsoft.VisualStudio.Enterprise.ASPNetHelper"
                        publicKeyToken="b03f5f7f11d50a3a"
                        culture="neutral"
                    />
                    <codeBase
                        version="10.0.0.0"
                        href="file:///C:/Program%20Files/Microsoft%20Visual%20Studio%2010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL"
                    />
                </dependentAssembly>
            </assemblyBinding>
        </runtime>
```

### <a name="to-add-the-profiler-post-process-step-to-the-configurationsystemwebcompilation-element"></a>Aby dodać krok po procesie profilera do elementu configuration/system.web/compilation

1. W razie potrzeby dodaj element **system.web** jako element podrzędny elementu **konfiguracji;** w przeciwnym razie przejdź do następnego kroku.

     Element **system.web** nie ma atrybutów. Element **konfiguracji** może mieć tylko jeden **element podrzędny system.web.**

2. W razie potrzeby dodaj element **kompilacji** jako element podrzędny elementu **system.web;** w przeciwnym razie przejdź do następnego kroku.

     Element **system.web** może mieć tylko jeden element **podrzędny kompilacji.**

3. Usuń wszystkie istniejące atrybuty z elementu **kompilacji** i dodaj następującą nazwę i wartość atrybutu:

    |Nazwa atrybutu|Wartość atrybutu|
    |--------------------|---------------------|
    |**assemblyPostProcessorType**|**Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter, Microsoft.VisualStudio.Enterprise.ASPNetHelper, Version=10.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a**|

```xml
    <configuration>
        <runtime>
        . . .
        </runtime>
        <system.web>
            <compilation
                assemblyPostProcessorType="Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter,
                    Microsoft.VisualStudio.Enterprise.ASPNetHelper,
                    Version=10.0.0.0,
                    Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
            />
        </system.web>
    <configuration>
```

### <a name="to-add-profiler-location-settings-to-the-configurationappsettings-element"></a>Aby dodać ustawienia lokalizacji profilera do elementu konfiguracja/appSettings

1. Jeśli to konieczne, dodaj **appSettings** element jako element podrzędny elementu **konfiguracji;** w przeciwnym razie przejdź do następnego kroku.

    **AppSettings** element nie ma atrybutów. Element **konfiguracji** może mieć tylko jeden **element podrzędny appSettings.**

2. Dodaj element **add** jako element podrzędny elementu **appSettings.**

3. Dodaj następujące nazwy i wartości atrybutów do elementu **add:**

   | Nazwa atrybutu | Wartość atrybutu |
   |----------------| - |
   | **key** | **Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation** |
   | **Wartość** | `PerformanceToolsFolder`**\VSInstr.Exe** |

4. Dodaj kolejny **element dodaj** jako element podrzędny **elementu appSettings.**

5. Dodaj następujące nazwy atrybutów i wartości do tego elementu **dodawania:**

   |Nazwa atrybutu|Wartość atrybutu|
   |--------------------|---------------------|
   |**key**|**Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools**|
   |**Wartość**|`PerformanceToolsFolder`|

    `PerformanceToolsFolder`to ścieżka plików wykonywalnych profilera. Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

```xml
    <configuration>
        <runtime>
        . . .
        </runtime>
        . . .
        <system.web>
        </system.web>
        <appSettings>
            <add
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation"
                value="C:\Program Files\Microsoft Visual Studio 14.0\Team Tools\Performance Tools\vsinstr.exe"
        />
            <add
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools"
                value="C:\Program Files\Microsoft Visual Studio 14.0\Team Tools\Performance Tools\"
            />
        </appSettings>
    </configuration>
```

## <a name="example"></a>Przykład
 Poniżej znajduje się kompletny plik *web.config,* który umożliwia instrumentację [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] i profilowanie dynamicznie skompilowanych aplikacji sieci Web. W tym przykładzie przyjęto założenie, że nie było żadnych innych ustawień w pliku przed modyfikacją.

```xml
<?xml version="1.0"?>
    <configuration>
        <runtime>
            <assemblyBinding
                xmlns="urn:schemas-microsoft-com:asm.v1"
            >
                <dependentAssembly>
                    <assemblyIdentity
                        name="Microsoft.VisualStudio.Enterprise.ASPNetHelper"
                        publicKeyToken="b03f5f7f11d50a3a"
                        culture="neutral"
                    />
                    <codeBase
                        version="10.0.0.0"
                        href="file:///C:/Program%20Files/Microsoft%20Visual%20Studio%2010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL"
                    />
                </dependentAssembly>
            </assemblyBinding>
        </runtime>
        <system.web>
            <compilation
                assemblyPostProcessorType="Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter,
                    Microsoft.VisualStudio.Enterprise.ASPNetHelper,
                    Version=10.0.0.0,
                    Culture=neutral,
                    PublicKeyToken=b03f5f7f11d50a3a"
            />
        </system.web>
        <appSettings>
            <add
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation"
                value="C:\Program Files\Microsoft Visual Studio 14.0\Team Tools\Performance Tools\vsinstr.exe"
            />
            <add
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools"
                value="C:\Program Files\Microsoft Visual Studio 14.0\Team Tools\Performance Tools\"
            />
        </appSettings>
    </configuration>

```

## <a name="see-also"></a>Zobacz też
- [Jak: Instrumentowanie dynamicznie skompilowanego ASP.NET aplikacji i zbieranie szczegółowych danych dotyczących chronometrażu](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)
- [Jak: Instrumentowanie dynamicznie skompilowanej aplikacji ASP.NET i zbieranie danych pamięci](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)
