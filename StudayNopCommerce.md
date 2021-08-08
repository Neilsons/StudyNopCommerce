# 学习NopCommerce第一节

1. 创建一个Mvc项目,手动创建然后选择mvc项目（选择有模型控制器的）。  
2. 第二步，从Nop.web主机开始入手进行修改，程序启动先从主机开始。
      - 对比使用模板创建的项目的主机和Nop.web的主机的区别  
        - 默认MVC主机代码

          ```csharp
            public class Program
              {
                  public static void Main(string[] args)
                  {
                      CreateHostBuilder(args).Build().Run();
                  }

                  public static IHostBuilder CreateHostBuilder(string[] args) =>
                      Host.CreateDefaultBuilder(args)
                          .ConfigureWebHostDefaults(webBuilder =>
                          {
                              webBuilder.UseStartup<Startup>();
                          });
              }
          ```

        - Nop.Web主机代码

            ``` csharp
            public class Program
            {
                /// <returns>A task that represents the asynchronous operation</returns>
                public static async Task Main(string[] args)
                {
                    //initialize the host
                    using var host = Host.CreateDefaultBuilder(args)
                        .UseServiceProviderFactory(new AutofacServiceProviderFactory())
                        .ConfigureWebHostDefaults(webBuilder => webBuilder
                            .ConfigureAppConfiguration(config =>
                            {
                                config
                                    .AddJsonFile(NopConfigurationDefaults.AppSettingsFilePath, true, true)
                                    .AddEnvironmentVariables();
                            })
                            .UseStartup<Startup>())
                        .Build();

                    //start the program, a task will be completed when the host starts
                    await host.StartAsync();

                    //a task will be completed when shutdown is triggered
                    await host.WaitForShutdownAsync();
                }
            }
            ```

        1. main方法异步执行
