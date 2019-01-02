---
title: ClickOnce niezarządzany wykaz interfejsów API | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
api_name:
- CleanOnlineAppCache
- GetDeploymentDataFromManifest
- LaunchApplication
api_location:
- dfshim.dll
api_type:
- COM
topic_type:
- apiref
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- LaunchApplication [ClickOnce unmanaged]
- ClickOnce, unmanaged APIs
- CleanOnlineAppCache [ClickOnce unmanaged]
- CleanOnlineAppCacheW interface [ClickOnce unmanaged]
- GetDeploymentDataFromManifest [ClickOnce unmanaged]
ms.assetid: ec002138-4054-456d-bcc1-79ac2f4a4fd7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 584dc441e54e89fea77667cac98cdad78bac5b2d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53968144"
---
# <a name="clickonce-unmanaged-api-reference"></a>ClickOnce niezarządzany wykaz interfejsów API
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] niezarządzane publiczne interfejsy API z dfshim.dll.  
  
## <a name="cleanonlineappcache"></a>CleanOnlineAppCache  
 Czyści lub odinstalowuje wszystkie aplikacje online z [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pamięci podręcznej aplikacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca wartość HRESULT reprezentujący błąd. Jeśli wystąpi wyjątek zarządzanych, zwraca 0x80020009 (DISP_E_EXCEPTION).  
  
### <a name="remarks"></a>Uwagi  
 Rozpocznie się wywołanie CleanOnlineAppCache [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] usługi, jeśli nie jest już uruchomiona.  
  
## <a name="getdeploymentdatafrommanifest"></a>GetDeploymentDataFromManifest  
 Pobiera informacje o wdrożeniu z manifestu i aktywacji adresu URL.  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|Typ|  
|---------------|-----------------|----------|  
|`pcwzActivationUrl`|Wskaźnik do `ActivationURL`.|LPCWSTR|  
|`pcwzPathToDeploymentManifest`|Wskaźnik do `PathToDeploymentManifest`.|LPCWSTR|  
|`pwzApplicationIdentity`|Wskaźnik do buforu do odbierania ciąg zakończony znakiem NULL określa zwracane tożsamości pełnej aplikacji.|LPWSTR|  
|`pdwIdentityBufferLength`|Wskaźnik do typu DWORD, która jest długością `pwzApplicationIdentity` buforu w WCHARs. Obejmuje to miejsce, w przypadku znaku NULL zakończenie.|LPDWORD|  
|`pwzProcessorArchitecture`|Wskaźnik do buforu, aby otrzymać ciąg zakończony znakiem NULL, który określa z architekturą procesora wdrożenie aplikacji z manifestu.|LPWSTR|  
|`pdwArchitectureBufferLength`|Wskaźnik do typu DWORD, która jest długością `pwzProcessorArchitecture` buforu w WCHARs.|LPDWORD|  
|`pwzApplicationManifestCodebase`|Wskaźnik do buforu, aby otrzymać ciąg zakończony zerem, który określa kodu w manifeście aplikacji z manifestu.|LPWSTR|  
|`pdwCodebaseBufferLength`|Wskaźnik do typu DWORD, która jest długością `pwzApplicationManifestCodebase` buforu w WCHARs.|LPDWORD|  
|`pwzDeploymentProvider`|Wskaźnik do buforu, aby otrzymać ciąg zakończony znakiem NULL, który określa dostawcę wdrożenia z manifestu, jeśli jest obecny. W przeciwnym razie zwracany jest pusty ciąg.|LPWSTR|  
|`pdwProviderBufferLength`|Wskaźnik do typu DWORD, która jest długością `pwzProviderBufferLength`.|LPDWORD|  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca wartość HRESULT reprezentujący błąd. Zwraca HRESULTFROMWIN32(ERROR_INSUFFICIENT_BUFFER), jeśli bufor jest za mały.  
  
### <a name="remarks"></a>Uwagi  
 Wskaźniki nie może mieć wartości null. `pcwzActivationUrl` i `pcwzPathToDeploymentManifest` nie może być pusta.  
  
 Odpowiada za wywołującego wyczyścić adresem URL aktywacji. Na przykład dodawanie ucieczki znaków, gdy są potrzebne lub usuwanie ciągu zapytania.  
  
 Odpowiada za wywołującego ograniczenia długości danych wejściowych. Na przykład maksymalna długość adresu URL jest 2KB.  
  
## <a name="launchapplication"></a>LaunchApplication  
 Uruchamia lub instaluje aplikację za pomocą adresu URL wdrożenia.  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|Typ|  
|---------------|-----------------|----------|  
|`deploymentUrl`|Wskaźnik na ciąg zakończony wartością NULL zawierający adres URL manifestu wdrażania.|LPCWSTR|  
|`data`|Zarezerwowane do użytku w przyszłości. Musi mieć wartość NULL.|LPVOID —|  
|`flags`|Zarezerwowane do użytku w przyszłości. Musi być równa 0.|DWORD|  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca wartość HRESULT reprezentujący błąd. Jeśli wystąpi wyjątek zarządzanych, zwraca 0x80020009 (DISP_E_EXCEPTION).  
  
## <a name="see-also"></a>Zobacz także  
 <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>