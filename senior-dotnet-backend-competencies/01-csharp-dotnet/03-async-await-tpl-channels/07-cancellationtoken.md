## CancellationToken
- Механизм отмены async-операций.
- `CancellationTokenSource` — источник, `.Cancel()`.
- `CancellationToken` — передаётся методам, проверяют `.IsCancellationRequested` или бросают `.ThrowIfCancellationRequested()`.
- При отмене — `OperationCanceledException` (TaskCanceledException).
