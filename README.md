CREATE SCHEMA IF NOT EXISTS `faculdade` DEFAULT CHARACTER SET utf8 ;
USE `faculdade` ;

CREATE TABLE IF NOT EXISTS `faculdade`.`cursos` (
  `id_cursos` INT NOT NULL AUTO_INCREMENT,
  `nome_curso` VARCHAR(45) NOT NULL,
  `codigo_curso` INT NOT NULL,
  `descricao` TEXT NULL,
  `carga_horaria_total` INT NOT NULL,
  PRIMARY KEY (`id_cursos`),
  UNIQUE INDEX `nome_curso_UNIQUE` (`nome_curso` ASC),
  UNIQUE INDEX `codigo_curso_UNIQUE` (`codigo_curso` ASC)
);

INSERT INTO `faculdade`.`cursos` (`nome_curso`, `codigo_curso`, `descricao`, `carga_horaria_total`) VALUES
('Engenharia de Software', 301, 'Formação em desenvolvimento de sistemas complexos', 4200),
('Administração de Empresas', 102, 'Formação em gestão e negócios', 3800),
('Direito', 501, 'Formação jurídica', 4500),
('Medicina', 601, 'Formação médica', 7200),
('Arquitetura e Urbanismo', 401, 'Formação em projeto e planejamento de espaços', 4000),
('Psicologia', 701, 'Formação em saúde mental e comportamento', 4000),
('Ciências Contábeis', 103, 'Formação em contabilidade e finanças', 3600),
('Jornalismo', 202, 'Formação em comunicação e notícias', 3400),
('Publicidade e Propaganda', 203, 'Formação em marketing e comunicação persuasiva', 3600),
('Economia', 104, 'Formação em análise econômica e mercados', 3800),
('Relações Internacionais', 502, 'Formação em política e economia global', 4000),
('Design Gráfico', 402, 'Formação em criação visual e comunicação', 3600),
('Gastronomia', 801, 'Formação em arte culinária e gestão de restaurantes', 3200),
('Enfermagem', 602, 'Formação em cuidados de saúde', 4000),
('Fisioterapia', 603, 'Formação em reabilitação física', 4000),
('Educação Física', 702, 'Formação em atividades físicas e esportes', 3200),
('História', 503, 'Formação em estudo do passado e da sociedade', 3200),
('Geografia', 504, 'Formação em estudo do espaço e do ambiente', 3200),
('Letras - Português/Inglês', 204, 'Formação em línguas e literatura', 3200),
('Pedagogia', 703, 'Formação em educação infantil e fundamental', 3600),
('Sistemas de Informação', 302, 'Formação em gestão de tecnologia da informação', 3800),
('Análise e Desenvolvimento de Sistemas', 303, 'Formação em desenvolvimento de software para web e mobile', 3600),
('Comércio Exterior', 105, 'Formação em negócios internacionais', 3600),
('Cinema e Audiovisual', 205, 'Formação em produção cinematográfica e audiovisual', 3800),
('Música', 802, 'Formação em performance e teoria musical', 3600);

CREATE TABLE IF NOT EXISTS `faculdade`.`alunos` (
  `id_alunos` INT NOT NULL AUTO_INCREMENT,
  `nome_completo` VARCHAR(45) NOT NULL,
  `data_de_nascimento` DATE NOT NULL,
  `endereco` VARCHAR(45) NOT NULL,
  `telefone` CHAR(11) NOT NULL,
  `numero_da_matricula` INT NOT NULL,
  `data_de_ingresso` DATE NOT NULL,
  `cursos_id_cursos` INT NOT NULL,
  PRIMARY KEY (`id_alunos`),
  UNIQUE INDEX `numero_da_matricula_UNIQUE` (`numero_da_matricula` ASC),
  INDEX `fk_alunos_cursos1_idx` (`cursos_id_cursos` ASC),
  CONSTRAINT `fk_alunos_cursos1`
    FOREIGN KEY (`cursos_id_cursos`)
    REFERENCES `faculdade`.`cursos` (`id_cursos`)
);

INSERT INTO `faculdade`.`alunos` (`nome_completo`, `data_de_nascimento`, `endereco`, `telefone`, `numero_da_matricula`, `data_de_ingresso`, `cursos_id_cursos`) VALUES
('Daniel Silva', '2002-05-10', 'Rua Armando Kan 92', '15156131115', 20231010, '2023-08-15', 3),
('Ana Souza', '2001-11-20', 'Avenida das Flores 123', '11987654321', 20222020, '2022-03-01', 1),
('Pedro Oliveira', '2003-03-05', 'Travessa da Paz 456', '21991234567', 20241030, '2024-08-10', 5),
('Mariana Costa', '2000-07-18', 'Alameda dos Bosques 789', '31988776655', 20211045, '2021-02-20', 7),
('Lucas Pereira', '2002-09-25', 'Praça da Liberdade 101', '41999887766', 20232050, '2023-08-25', 9),
('Julia Rodrigues', '2001-04-02', 'Rua das Estrelas 222', '19987651234', 20221060, '2022-03-10', 11),
('Gabriel Almeida', '2003-12-15', 'Avenida Brasil 333', '27991237890', 20242075, '2024-08-18', 13),
('Beatriz Ferreira', '2000-06-30', 'Travessa do Sol 444', '35988770011', 20212080, '2021-03-01', 15),
('Rafael Gomes', '2002-08-08', 'Alameda dos Ipês 555', '47999881122', 20231090, '2023-09-01', 17),
('Isabela Martins', '2001-03-22', 'Praça da Bandeira 666', '12987652345', 20222100, '2022-03-15', 19),
('Thiago Castro', '2003-11-05', 'Rua dos Cravos 777', '22991238901', 20241115, '2024-09-05', 21),
('Luana Rocha', '2000-05-12', 'Avenida Paulista 888', '33988772233', 20211120, '2021-03-10', 23),
('Vinicius Barbosa', '2002-07-28', 'Travessa das Acácias 999', '49999883344', 20232135, '2023-09-10', 25),
('Amanda Azevedo', '2001-02-10', 'Alameda dos Jasmins 1010', '13987653456', 20221140, '2022-03-20', 2),
('Gustavo Vargas', '2003-10-20', 'Praça da Sé 1111', '28991239012', 20242155, '2024-09-15', 4),
('Camila Nunes', '2000-04-05', 'Rua Augusta 1212', '37988774455', 20212160, '2021-03-25', 6),
('Bruno Souza', '2002-06-18', 'Avenida Ipiranga 1313', '45999885566', 20231170, '2023-09-20', 8),
('Jessica Oliveira', '2001-01-25', 'Travessa da Consolação 1414', '17987654567', 20222185, '2022-03-30', 10),
('Felipe Costa', '2003-09-02', 'Alameda Santos 1515', '29991230123', 20241190, '2024-09-25', 12),
('Natália Pereira', '2000-03-10', 'Praça da República 1616', '39988775678', 20211200, '2021-04-01', 14),
('Ricardo Almeida', '2002-05-25', 'Rua da Bahia 1717', '41999886789', 20232215, '2023-10-01', 16),
('Juliana Ferreira', '2001-12-01', 'Avenida Rio Branco 1818', '19987656789', 20221220, '2022-04-05', 18),
('Marcelo Gomes', '2003-08-15', 'Travessa do Ouvidor 1919', '27991231234', 20242235, '2024-10-05', 20),
('Patrícia Martins', '2000-02-20', 'Alameda Ministro Rocha Azevedo 2020', '35988777890', 20212240, '2021-04-10', 22),
('Eduardo Castro', '2002-04-02', 'Praça Roosevelt 2121', '47999882345', 20231250, '2023-10-10', 24);

CREATE TABLE IF NOT EXISTS `faculdade`.`materias` (
  `id_materias` INT NOT NULL AUTO_INCREMENT,
  `nome_materia` VARCHAR(45) NOT NULL,
  `codigo_materia` INT NOT NULL,
  `descricao` TEXT NULL,
  `carga_horaria` INT NULL,
  `cursos_id_cursos` INT NOT NULL,
  PRIMARY KEY (`id_materias`),
  UNIQUE INDEX `codigo_materia_UNIQUE` (`codigo_materia` ASC),
  UNIQUE INDEX `nome_materia_UNIQUE` (`nome_materia` ASC),
  INDEX `fk_materias_cursos1_idx` (`cursos_id_cursos` ASC),
  CONSTRAINT `fk_materias_cursos1`
    FOREIGN KEY (`cursos_id_cursos`)
    REFERENCES `faculdade`.`cursos` (`id_cursos`)
);

INSERT INTO `faculdade`.`materias` (`nome_materia`, `codigo_materia`, `descricao`, `carga_horaria`, `cursos_id_cursos`) VALUES
('Programação Orientada a Objetos', 301101, 'Conceitos e prática de POO', 80, 1),
('Cálculo I', 301102, 'Fundamentos do cálculo diferencial e integral', 90, 1),
('Álgebra Linear', 301103, 'Matrizes, vetores e espaços vetoriais', 70, 1),
('Gestão de Projetos', 102101, 'Metodologias e ferramentas de gestão', 60, 2),
('Marketing Estratégico', 102102, 'Planejamento e estratégias de marketing', 75, 2),
('Direito Civil', 501101, 'Princípios e normas do direito civil', 90, 3),
('Anatomia Humana', 601101, 'Estrutura e funcionamento do corpo humano', 120, 4),
('Projeto Arquitetônico', 401101, 'Conceitos e desenvolvimento de projetos', 100, 5),
('Psicologia Geral', 701101, 'Introdução aos conceitos da psicologia', 70, 6),
('Contabilidade Básica', 103101, 'Princípios e lançamentos contábeis', 80, 7),
('Teoria do Jornalismo', 202101, 'Fundamentos e história do jornalismo', 60, 8),
('Comunicação Integrada', 203101, 'Estratégias de comunicação e marketing', 75, 9),
('Microeconomia', 104101, 'Princípios da oferta e demanda', 70, 10),
('Política Internacional', 502101, 'Teorias e atores das relações internacionais', 80, 11),
('Desenho Técnico', 402101, 'Técnicas de representação gráfica', 60, 12),
('Técnicas de Cozinha', 801101, 'Fundamentos da culinária', 90, 13),
('Fisiologia Humana', 602101, 'Funcionamento dos sistemas do corpo humano', 100, 14),
('Cinesiologia', 603101, 'Estudo do movimento humano', 70, 15),
('Bioquímica', 702101, 'Química dos processos biológicos', 80, 16),
('História do Brasil', 503101, 'Evolução histórica da sociedade brasileira', 75, 17),
('Geografia Humana', 504101, 'Estudo das relações entre sociedade e espaço', 70, 18),
('Literatura Brasileira', 204101, 'Panorama da literatura nacional', 80, 19),
('Didática', 703101, 'Teorias e práticas de ensino', 60, 20),
('Banco de Dados', 302101, 'Modelagem e gerenciamento de bancos de dados', 80, 21),
('Engenharia de Requisitos', 303101, 'Técnicas de elicitação e especificação', 70, 22);

CREATE TABLE IF NOT EXISTS `faculdade`.`turmas` (
  `id_turmas` INT NOT NULL AUTO_INCREMENT,
  `nome_da_turma` VARCHAR(45) NOT NULL,
  `horario` INT NOT NULL,
  `periodo_letivo` VARCHAR(45) NOT NULL,
  `capacidade_maxima` INT NOT NULL,
  `cursos_id_cursos` INT NOT NULL,
  `materias_id_materias` INT NOT NULL,
  PRIMARY KEY (`id_turmas`),
  UNIQUE INDEX `nome_da_turma_UNIQUE` (`nome_da_turma` ASC),
  INDEX `fk_turmas_cursos1_idx` (`cursos_id_cursos` ASC),
  INDEX `fk_turmas_materias1_idx` (`materias_id_materias`),
  CONSTRAINT `fk_turmas_cursos1`
    FOREIGN KEY (`cursos_id_cursos`)
    REFERENCES `faculdade`.`cursos` (`id_cursos`),
  CONSTRAINT `fk_turmas_materias1`
    FOREIGN KEY (`materias_id_materias`)
    REFERENCES `faculdade`.`materias` (`id_materias`)
);

INSERT INTO `faculdade`.`turmas` (`nome_da_turma`, `horario`, `periodo_letivo`, `capacidade_maxima`, `cursos_id_cursos`, `materias_id_materias`) VALUES
('A1', 8, '2025.1', 40, 1, 1),
('B2', 10, '2025.1', 35, 2, 4),
('C3', 14, '2025.1', 50, 3, 6),
('D4', 16, '2025.1', 45, 4, 7),
('E5', 19, '2025.1', 30, 5, 8),
('F1', 8, '2025.1', 40, 6, 9),
('G2', 10, '2025.1', 35, 7, 10),
('H3', 14, '2025.1', 50, 8, 11),
('I4', 16, '2025.1', 45, 9, 12),
('J5', 19, '2025.1', 30, 10, 13),
('K1', 8, '2025.2', 40, 11, 14),
('L2', 10, '2025.2', 35, 12, 15),
('M3', 14, '2025.2', 50, 13, 16),
('N4', 16, '2025.2', 45, 14, 17),
('O5', 19, '2025.2', 30, 15, 18),
('P1', 8, '2025.2', 40, 16, 19),
('Q2', 10, '2025.2', 35, 17, 20),
('R3', 14, '2025.2', 50, 18, 21),
('S4', 16, '2025.2', 45, 19, 22),
('T5', 19, '2025.2', 30, 20, 23),
('U1', 8, '2026.1', 40, 21, 24),
('V2', 10, '2026.1', 35, 22, 25),
('W3', 14, '2026.1', 50, 1, 2),
('X4', 16, '2026.1', 45, 2, 3),
('Y5', 19, '2026.1', 30, 3, 5);

CREATE TABLE IF NOT EXISTS `faculdade`.`notas` (
  `id_notas` INT NOT NULL AUTO_INCREMENT,
  `nome_avaliacao` VARCHAR(45) NOT NULL,
  `notas` DECIMAL(10,2) NOT NULL,
  `data_avaliacao` DATE NOT NULL,
  `alunos_id_alunos` INT NOT NULL,
  `turmas_id_turmas` INT NOT NULL,
  PRIMARY KEY (`id_notas`),
  INDEX `fk_notas_alunos1_idx` (`alunos_id_alunos` ASC),
  INDEX `fk_notas_turmas1_idx` (`turmas_id_turmas` ASC),
  CONSTRAINT `fk_notas_alunos1`
    FOREIGN KEY (`alunos_id_alunos`)
    REFERENCES `faculdade`.`alunos` (`id_alunos`),
  CONSTRAINT `fk_notas_turmas1`
    FOREIGN KEY (`turmas_id_turmas`)
    REFERENCES `faculdade`.`turmas` (`id_turmas`)
);

INSERT INTO `faculdade`.`notas` (`nome_avaliacao`, `notas`, `data_avaliacao`, `alunos_id_alunos`, `turmas_id_turmas`) VALUES
('Prova 1', 8.50, '2025-03-15', 1, 1),
('Trabalho 1', 9.00, '2025-03-22', 2, 2),
('Prova 2', 7.80, '2025-04-05', 3, 3),
('Participação', 9.50, '2025-04-12', 4, 4),
('Prova Final', 8.20, '2025-05-03', 5, 5),
('Prova 1', 7.00, '2025-03-18', 6, 6),
('Trabalho 1', 8.80, '2025-03-25', 7, 7),
('Prova 2', 9.20, '2025-04-08', 8, 8),
('Participação', 8.50, '2025-04-15', 9, 9),
('Prova Final', 7.50, '2025-05-05', 10, 10),
('Prova 1', 9.10, '2025-03-20', 11, 11),
('Trabalho 1', 8.00, '2025-03-27', 12, 12),
('Prova 2', 7.30, '2025-04-10', 13, 13),
('Participação', 9.80, '2025-04-17', 14, 14),
('Prova Final', 8.90, '2025-05-07', 15, 15),
('Prova 1', 6.50, '2025-03-22', 16, 16),
('Trabalho 1', 9.30, '2025-03-29', 17, 17),
('Prova 2', 8.60, '2025-04-12', 18, 18),
('Participação', 7.90, '2025-04-19', 19, 19),
('Prova Final', 9.40, '2025-05-09', 20, 20),
('Prova 1', 8.80, '2025-03-24', 21, 21),
('Trabalho 1', 7.60, '2025-03-31', 22, 22),
('Prova 2', 9.00, '2025-04-14', 23, 23),
('Participação', 8.20, '2025-04-21', 24, 24),
('Prova Final', 7.10, '2025-05-11', 25, 25);

CREATE TABLE IF NOT EXISTS `faculdade`.`professores` (
  `id_professores` INT NOT NULL AUTO_INCREMENT,
  `nome_completo` VARCHAR(45) NOT NULL,
  `data_de_nascimento` DATE NULL,
  `telefone` CHAR(11) NOT NULL,
  `especializacao` VARCHAR(45) NOT NULL,
  `titulacao` VARCHAR(45) NOT NULL,
  PRIMARY KEY (`id_professores`),
  UNIQUE INDEX `telefone_UNIQUE` (`telefone` ASC)
);

INSERT INTO `faculdade`.`professores` (`nome_completo`, `data_de_nascimento`, `telefone`, `especializacao`, `titulacao`) VALUES
('Carlos Alberto', '1975-08-12', '11912345678', 'Engenharia de Software', 'Doutor'),
('Maria Fernanda', '1982-03-25', '21987654321', 'Administração de Empresas', 'Mestre'),
('José Roberto', '1969-11-01', '31991237890', 'Direito Civil', 'Doutor'),
('Ana Paula', '1978-06-15', '41988770011', 'Anatomia Humana', 'Mestre'),
('Ricardo Mendes', '1985-09-20', '19999881122', 'Projeto Arquitetônico', 'Doutor'),
('Patrícia Souza', '1980-01-30', '27987652345', 'Psicologia Clínica', 'Mestre'),
('Fernando Oliveira', '1972-05-05', '35991238901', 'Contabilidade Gerencial', 'Doutor'),
('Camila Rocha', '1988-10-18', '47988773456', 'Teoria da Comunicação', 'Mestre'),
('Marcelo Costa', '1977-02-28', '12999884567', 'Marketing Digital', 'Doutor'),
('Juliana Pereira', '1983-07-07', '22987655678', 'Economia Política', 'Mestre'),
('Eduardo Almeida', '1970-12-22', '33991236789', 'Relações Internacionais', 'Doutor'),
('Luciana Gomes', '1986-04-03', '49988777890', 'Design de Interfaces', 'Mestre'),
('Sérgio Martins', '1979-09-10', '13999888901', 'Gastronomia Funcional', 'Doutor'),
('André Castro', '1981-01-15', '28987659012', 'Enfermagem Intensiva', 'Mestre'),
('Mariana Ribeiro', '1987-05-25', '37991230123', 'Fisioterapia Esportiva', 'Doutor'),
('Gustavo Ferreira', '1973-11-30', '45988771234', 'Educação Física Escolar', 'Mestre'),
('Renata Nunes', '1989-03-05', '17999882345', 'História Moderna', 'Doutor'),
('Vinicius Barbosa', '1976-07-18', '29987653456', 'Geografia Urbana', 'Mestre'),
('Aline Azevedo', '1984-12-01', '39991234567', 'Linguística Aplicada', 'Doutor'),
('Roberto Vargas', '1971-04-12', '41988775678', 'Didática do Ensino Superior', 'Mestre'),
('Carla Mendes', '1988-08-20', '15999886789', 'Sistemas de Informação', 'Doutor'),
('Paulo Oliveira', '1974-02-10', '21987657890', 'Análise de Sistemas', 'Mestre'),
('Simone Costa', '1990-06-25', '31991238901', 'Comércio Exterior', 'Doutor'),
('Márcio Rocha', '1979-10-05', '47988779012', 'Produção Audiovisual', 'Mestre'),
('Fernanda Souza', '1982-01-20', '12999880123', 'Teoria Musical', 'Doutor');

CREATE TABLE IF NOT EXISTS `faculdade`.`turmas_has_professores` (
  `turmas_id_turmas` INT NOT NULL,
  `professores_id_professores` INT NOT NULL,
  PRIMARY KEY (`turmas_id_turmas`, `professores_id_professores`),
  INDEX `fk_turmas_has_professores_professores1_idx` (`professores_id_professores` ASC),
  INDEX `fk_turmas_has_professores_turmas1_idx` (`turmas_id_turmas` ASC),
  CONSTRAINT `fk_turmas_has_professores_turmas1`
    FOREIGN KEY (`turmas_id_turmas`)
    REFERENCES `faculdade`.`turmas` (`id_turmas`),
  CONSTRAINT `fk_turmas_has_professores_professores1`
    FOREIGN KEY (`professores_id_professores`)
    REFERENCES `faculdade`.`professores` (`id_professores`)
);

INSERT INTO `faculdade`.`turmas_has_professores` (`turmas_id_turmas`, `professores_id_professores`) VALUES
(1, 1),
(2, 2),
(3, 3),
(4, 4),
(5, 5),
(6, 6),
(7, 7),
(8, 8),
(9, 9),
(10, 10),
(11, 11),
(12, 12),
(13, 13),
(14, 14),
(15, 15),
(16, 16),
(17, 17),
(18, 18),
(19, 19),
(20, 20),
(21, 21),
(22, 22),
(23, 1),
(24, 2),
(25, 3);
