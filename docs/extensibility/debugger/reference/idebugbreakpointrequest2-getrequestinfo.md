---
title: IDebugBreakpointRequest2::GetRequestInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest2::GetRequestInfo
helpviewer_keywords:
- IDebugBreakpointRequest2::GetRequestInfo
ms.assetid: 5defd8d7-6daa-479b-8909-fcc4ae0b357a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3523c72fa1a7ea14fbf1b4a69caf04cfebb82911
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352897"
---
# <a name="idebugbreakpointrequest2getrequestinfo"></a>IDebugBreakpointRequest2::GetRequestInfo
Obtiene la información de solicitud de punto de interrupción que describe esta solicitud de punto de interrupción.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetRequestInfo( 
   BPREQI_FIELDS    dwFields,
   BP_REQUEST_INFO* pBPRequestInfo
);
```

```csharp
int GetRequestInfo( 
   eunm_BPREQI_FIELDS  dwFields,
   BP_REQUEST_INFO[]   pBPRequestInfo
);
```

## <a name="parameters"></a>Parámetros
`dwFields`\
[in] Una combinación de marcas de la [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) enumeración que determina qué campos de la `pBPRequestInfo` parámetro son para rellenarlo.

`pBPRequestInfo`\
[out] Especifica el [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) estructura que se rellena con la descripción de la solicitud de punto de interrupción.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra cómo implementar este método para una sencilla `CDebugBreakpointRequest` objeto que expone el [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) interfaz.

```
HRESULT CDebugBreakpointRequest::GetRequestInfo(
   BPREQI_FIELDS    dwFields,
   BP_REQUEST_INFO* pBPRequestInfo)
{
   HRESULT hr;

   if (pBPRequestInfo)
   {
      // Copy the specified fields of the request info from the class
      // member variable to the local BP_REQUEST_INFO variable.
      hr = CopyBP_REQUEST_INFO(m_bpRequestInfo,
                               *pBPRequestInfo, dwFields);
   }
   else
   {
      hr = E_INVALIDARG;
   }

   return hr;
}

HRESULT CDebugBreakpointRequest::CopyBP_REQUEST_INFO(
   BP_REQUEST_INFO& bpReqSrc,
   BP_REQUEST_INFO& bpReqDest,
   DWORD dwFields)
{
   HRESULT hr = S_OK;

   // Start with a raw copy.
   memcpy(&bpReqDest, &bpReqSrc, sizeof (BP_REQUEST_INFO));

   // The fields in the destination are the result of the AND of
   // bpReqSrc.dwFields and dwFields.
   bpReqDest.dwFields = dwFields & bpReqSrc.dwFields;

   // Fill in the bp location information if the BPREQI_BPLOCATION flag is
   // set in BPREQI_FIELDS.
   if (IsFlagSet(bpReqDest.dwFields, BPREQI_BPLOCATION))
   {
      // Switch based on the BP_LOCATION_TYPE.
      switch (bpReqSrc.bpLocation.bpLocationType)
      {
         case BPLT_CODE_FILE_LINE:
         {
            // Copy the bstrContext and AddRef the IDebugDocumentPosition2
            // of the BP_LOCATION_CODE_FILE_LINE structure.
            bpReqDest.bpLocation.bpLocation.bplocCodeFileLine.bstrContext =
               SysAllocString(bpReqSrc.bpLocation.bpLocation.bplocCodeFileLine.bstrContext);
            bpReqDest.bpLocation.bpLocation.bplocCodeFileLine.pDocPos->AddRef();
            break;
         }
         case BPLT_CODE_FUNC_OFFSET:
         {
            // Copy the bstrContext and AddRef the IDebugFunctionPosition2
            // of the BP_LOCATION_CODE_FUNC_OFFSET structure.
            bpReqDest.bpLocation.bpLocation.bplocCodeFuncOffset.bstrContext =
               SysAllocString(bpReqSrc.bpLocation.bpLocation.bplocCodeFuncOffset.bstrContext);
            bpReqDest.bpLocation.bpLocation.bplocCodeFuncOffset.pFuncPos->AddRef();
            break;
         }
         case BPLT_CODE_CONTEXT:
         {
            // AddRef the IDebugCodeContext2 of the BP_LOCATION_CODE_CONTEXT
            // structure.
            bpReqDest.bpLocation.bpLocation.bplocCodeContext.pCodeContext->AddRef();
            break;
         }
         case BPLT_CODE_STRING:
         {
            // Copy the bstrContext and bstrCodeExpr of the BP_LOCATION_CODE_STRING
            // structure.
            bpReqDest.bpLocation.bpLocation.bplocCodeString.bstrContext =
               SysAllocString(bpReqSrc.bpLocation.bpLocation.bplocCodeString.bstrContext);
            bpReqDest.bpLocation.bpLocation.bplocCodeString.bstrCodeExpr =
               SysAllocString(bpReqSrc.bpLocation.bpLocation.bplocCodeString.bstrCodeExpr);
            break;
         }
         case BPLT_CODE_ADDRESS:
         {
            // Copy the bstrContext, bstrModuleUrl, bstrFunction, and bstrAddress
            // of the BP_LOCATION_CODE_ADDRESS structure.
            bpReqDest.bpLocation.bpLocation.bplocCodeAddress.bstrContext =
               SysAllocString(bpReqSrc.bpLocation.bpLocation.bplocCodeAddress.bstrContext);
            bpReqDest.bpLocation.bpLocation.bplocCodeAddress.bstrModuleUrl =
               SysAllocString(bpReqSrc.bpLocation.bpLocation.bplocCodeAddress.bstrModuleUrl);
            bpReqDest.bpLocation.bpLocation.bplocCodeAddress.bstrFunction =
               SysAllocString(bpReqSrc.bpLocation.bpLocation.bplocCodeAddress.bstrFunction);
            bpReqDest.bpLocation.bpLocation.bplocCodeAddress.bstrAddress =
               SysAllocString(bpReqSrc.bpLocation.bpLocation.bplocCodeAddress.bstrAddress);
            break;
         }
         case BPLT_DATA_STRING:
         {
            // Conditional AddRef of the IDebugThread2 of the BP_LOCATION_DATA_STRING
            // structure.
            if (bpReqDest.bpLocation.bpLocation.bplocDataString.pThread)
            {
               bpReqDest.bpLocation.bpLocation.bplocDataString.pThread->AddRef();
            }
            // Copy the bstrContext and bstrDataExpr of the BP_LOCATION_DATA_STRING
            // structure.
            bpReqDest.bpLocation.bpLocation.bplocDataString.bstrContext =
                  SysAllocString(bpReqSrc.bpLocation.bpLocation.bplocDataString.bstrContext);
            bpReqDest.bpLocation.bpLocation.bplocDataString.bstrDataExpr =
                  SysAllocString(bpReqSrc.bpLocation.bpLocation.bplocDataString.bstrDataExpr);
            break;
         }
         case BPLT_RESOLUTION:
         {
            // AddRef of the IDebugBreakpointResolution2 of the BP_LOCATION_RESOLUTION
            // structure.
            bpReqDest.bpLocation.bpLocation.bplocResolution.pResolution->AddRef();
            break;
         }
         default:
         {
            assert(FALSE);
            // Clear the BPREQI_BPLOCATION flag in the BPREQI_FIELDS of the
            // destination BP_REQUEST_INFO.
            ClearFlag(bpReqDest.dwFields, BPREQI_BPLOCATION);
            break;
         }
      }
   }
   // AddRef the IDebugProgram2 if the BPREQI_PROGRAM flag is set in BPREQI_FIELDS.
   if (IsFlagSet(bpReqDest.dwFields, BPREQI_PROGRAM))
   {
      bpReqDest.pProgram->AddRef();
   }
   // Copy the bstrProgramName if the BPREQI_PROGRAMNAME flag is set in BPREQI_FIELDS.
   if (IsFlagSet(bpReqDest.dwFields, BPREQI_PROGRAMNAME))
   {
      bpReqDest.bstrProgramName = SysAllocString(bpReqSrc.bstrProgramName);
   }
   // AddRef the IDebugThread2 if the BPREQI_THREAD flag is set in BPREQI_FIELDS.
   if (IsFlagSet(bpReqDest.dwFields, BPREQI_THREAD))
   {
      bpReqDest.pThread->AddRef();
   }
   // Copy the bstrThreadName if the BPREQI_THREADNAME flag is set in BPREQI_FIELDS.
   if (IsFlagSet(bpReqDest.dwFields, BPREQI_THREADNAME))
   {
      bpReqDest.bstrThreadName = SysAllocString(bpReqSrc.bstrThreadName);
   }
   // Check to see if the BPREQI_CONDITION flag is set in BPREQI_FIELDS.
   if (IsFlagSet(bpReqDest.dwFields, BPREQI_CONDITION))
   {
      // Conditional AddRef of the IDebugThread2 of the BP_CONDITION structure.
      if (bpReqDest.bpCondition.pThread)
      {
         bpReqDest.bpCondition.pThread->AddRef();
      }
      // Copy the bstrContext and bstrCondition of the BP_CONDITION structure.
      bpReqDest.bpCondition.bstrContext = SysAllocString(bpReqSrc.bpCondition.bstrContext);
      bpReqDest.bpCondition.bstrCondition = SysAllocString(bpReqSrc.bpCondition.bstrCondition);
   }

   return hr;
}
```

## <a name="see-also"></a>Vea también
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)