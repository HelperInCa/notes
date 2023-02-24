


func UpdateBackup(userId, clusterUuid string) error {
   wc, err := webserver.GetRequestClient(userId)
   if err != nil {
      return fmt.Errorf("DoWebserverClient: get webserver client failed: %v", err)
   }
   strategy, err := webserver.GetBackupStrategyByClusterUuid(wc, clusterUuid)
   if err != nil {
      return fmt.Errorf("DoGetBackupStrategy: get backup strategy failed %v", err)
   }
   minute := int(time.Now().Add(time.Minute * 5).Minute())
   hour := int(time.Now().Add(time.Minute * 5).Hour())
   fullWeek := int(time.Now().Add(time.Minute * 5).Weekday())
   fullBackup := fmt.Sprintf("%d %d * * %d", minute, hour, fullWeek)
   increWeek := (fullWeek + 3) % 7
   increBackup := fmt.Sprintf("%d %d * * %d", minute, hour, increWeek)
   strategy.FullBackup = fullBackup
   strategy.IncBackup = increBackup
   if err := webserver.UpdateBackupStrategyByClusterUuid(wc, clusterUuid, strategy); err != nil {
      return fmt.Errorf("DoWebserverClient: update order failed %v. ", err)
   }
   return nil
}
